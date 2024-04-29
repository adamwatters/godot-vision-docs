---
slug: /road-map
title: Road Map
---

# Roadmap

[Contributions](https://github.com/kevinw/GodotVision) welcome!

## Future Features

Some things we'll add in the near future:

### Live Reload

Saving a scene, or modifying a resource in the editor could show in the headset immediately, without having to recompile/redeploy/rerun the Xcode project. Iteration time in gamedev is important!

<video controls>
    <source src="/img/live_reload.mp4"></source>
</video>

### Leverage [groups](https://docs.godotengine.org/en/stable/tutorials/scripting/groups.html) and layers more

We could provide an API to prevent a subset of your Godot scene from being rendered by RealityKit by definiing a "Reality-Kit-hidden" group, for example.

### Run Godot on background thread (optionally)

RealityKit is a relatively heavyweight presence on the main thread. It could be beneficial to have an option to use all those Apple Silicon cores to run Godot on a background thread for more parallelism, and faster framerates.

### Implement more Godot Nodes

Some Godot nodes are currently unimplemented but would be useful/performant to have RealityKit versions of:

- [GridMap](https://docs.godotengine.org/en/stable/tutorials/3d/using_gridmaps.html)
- [MultiMeshInstance3D](https://docs.godotengine.org/en/stable/classes/class_multimeshinstance3d.html)

### Static library dependencies

Adding GodotVision as a package dependency currently means for a fresh build, you must build SwiftGodot, SwiftGodotKit, and GodotVision from source. We could provide a `.xcframework` for GodotVision with ready-to-use build artifacts ready for simulator and device builds, reducing your game's initial build time.

### Integration with [Godot XR Tools](https://godotvr.github.io/godot-xr-tools/)

See what concepts can map cleanly to the Vision Pro world.

## Someday...maybe...?

* Use (or support optionally?) a non-headless (ideally, Metal) rendering server. Then we could render 2D viewports (for things like worldspace UI or cameras-rendering-to-textures).

* Add an implementation of Godot's [high-level multiplayer](https://docs.godotengine.org/en/stable/tutorials/networking/high_level_multiplayer.html) based on Apple's [GroupSession](https://developer.apple.com/documentation/groupactivities/groupsession) abstraction so that making Godot experiences shared over Persona Facetime calls is effortless.

* Document and simplify the process to build the whole stack, starting with Godot, so that users can easily make slim builds including [only the Godot features they need](https://docs.godotengine.org/en/stable/contributing/development/compiling/optimizing_for_size.html#disabling-unwanted-modules).