---
slug: /road-map
title: Road Map
---

# Roadmap

[Contributions](https://github.com/kevinw/GodotVision) welcome!

## Future Features

**Live Reload**: saving a scene, or modifying a resource in the editor could show in the headset immediately, without having to recompile/redeploy/rerun the Xcode project. Iteration time in gamedev is important!

**Run Godot on background thread**: RealityKit is a relatively heavyweight presence on the main thread. It could be beneficial to have an option to use all those Apple Silicon cores to run Godot on a background thread for more parallelism.

**Implement more Godot Nodes**: Some Godot nodes are currently unimplemented but would be useful/performant to have RealityKit versions of:

- [GridMap](https://docs.godotengine.org/en/stable/tutorials/3d/using_gridmaps.html)
- [MultiMeshInstance3D](https://docs.godotengine.org/en/stable/classes/class_multimeshinstance3d.html)

**Static library dependencies**: Adding GodotVision as a package dependency currently means for a fresh build, you must build SwiftGodot, SwiftGodotKit, and GodotVision from source. We could provide a `.xcframework` for GodotVision with ready-to-use build artifacts ready for simulator and device builds, reducing your game's initial build time.