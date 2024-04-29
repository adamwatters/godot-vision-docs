---
slug: /guides/volume-camera
title: Volume Camera
---

# Volume Camera

---

## Objective

You will understand how to define the part of your Godot scene rendered on visionOS.

---

## Quick Guide

If you have a copy of GodotVisionExample and you want to change the area rendered in visionOS, you'll need to make **two updates**.

First, on the Godot side, open the `VisionVolumeCamera` scene instantiated in the main scene. Update the dimensions of the `BoxShape3D` inside the `CollisionShape3D`.

![a short gif of a visionOS game](/img/volume-camera-1.png)

Second, update the `VOLUME_SIZE` constant set in `GodotVisionExample.swift`.

🚨 The scale can differ, but the ratio of the dimensions set in Godot and Swift must match. 🚨

```
// GodotVisionExample.swift

let VOLUME_SIZE = simd_double3(1.8, 1.0, 1.5) // <-- change these values

@main
struct GodotVisionExample: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
        .windowStyle(.volumetric)
        .defaultSize(width: VOLUME_SIZE.x, height: VOLUME_SIZE.y, depth: VOLUME_SIZE.z, in: .meters)
    }
}
```

---

## Volume Camera Details

### visionOS volumes

Currently, all GodotVision apps are rendered inside visionOS volumes.

A [volume](https://developer.apple.com/documentation/SwiftUI/WindowStyle/volumetric), is a special visionOS window for displaying 3D content in a bounded region. Content that falls outside of the volume is clipped.

The size of a volume is set with a `defaultSize` scene modifier - see the code block just a little ways back up the page ☝️.

### GodotVision Volume Camera

GodotVision uses a Volume Camera to position your Godot scene within a volume.

The Volume Camera isn't particularly special - it's an [`Area3D`](https://docs.godotengine.org/en/stable/classes/class_area3d.html) named **VisionVolumeCamera** containing a [`CollisionShape3D`](https://docs.godotengine.org/en/stable/classes/class_collisionshape3d.html).

For convenience, the Volume Camera in GodotVisionExample also contains a Godot `Camera3D` so you can simulate the visionOS perspective when testing your game in Godot.

The `CollisionShape3D`'s shape property is set to a `BoxShape3D`. The dimensions of that box represent the area of your Godot scene that fall within the bounds of the target visionOS volume.

The position, rotation, and scale of the **VisionVolumeCamera** node determine how the RealityKit clone of your Godot scene is transformed within the visionOS volume.

### Syncing the Volume Camera and visionOS volume

To ensure the expected Godot content is inside the visionOS volume, GodotVision checks that dimension ratios match between the volume and the Volume Camera. If they don't you should see this error in the XCode console:

⚠️ `changeScaleIfVolumeSizeChanged ERROR: expected the proportions of the RealityKit volume to match the godot volume! the camera volume may be off.`

If you've checked your dimensions and you don't think you should be seeing this error, your volume size might fall outside the undocumented max and minimum volume sizes. All volume dimensions must fall **between 0.24 and 1.98 meters**.


