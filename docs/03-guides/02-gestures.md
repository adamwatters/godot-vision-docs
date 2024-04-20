---
slug: /guides/gestures
title: Spatial Gestures
---

# Spatial Gestures

You can easily let players pinch and drag objects in the world. 

## Signals

### `spatial_drag` signal

Any `CollisionObject3D` with a signal named `spatial_drag` will receive drag gesture events from GodotVision. The signal gets called with a Dictionary with the following parameters:

```
{
    "phase": String,                       // "began", "changed", or "ended"
    "global_transform": Transform3D,       // the current Transform3D of the Node
    "start_global_transform": Transform3D, // the Transform3D of the Node when the gesture began
}
```

## Example Drag Script

Below is a simple version of a "drag" gdscript from the GodotVisionExample "hello" scene. If you attach this to a `CollisionObject3D` (like an `Area3D` or a `AnimatableBody3D` or a `StaticBody3D`), you can gaze at the object, pinch, and move your hand to translate and rotate it!

```
extends Node

signal spatial_drag(Dictionary)

func _ready():
	spatial_drag.connect(on_spatial_drag)
	
func _exit_tree():
	spatial_drag.disconnect(on_spatial_drag)

func on_spatial_drag(params: Dictionary):
	self.global_transform = params['global_transform'] # Move in 3D with the spatial gesture.
```
