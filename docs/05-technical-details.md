---
slug: /technical-details
title: Technical Details
---

# Technical Details

A peek under the hood!

:::note

Details are changing rapidly. Check out the [repository](https://github.com/kevinw/GodotVision)!

:::

## How Godot and RealityKit combine

Godot has been modified to exist as an embedded library in a RealityKit app (see [Dependencies](#dependencies) below).

We run Godot in "`--headless`" mode ([details here](https://docs.godotengine.org/en/stable/tutorials/export/exporting_for_dedicated_servers.html)) which means that all graphics and windows are disabled.

Then, every RealityKit frame, we call into Godot to pass it input, and to ask it to "tick" its world forward. 

When new Godot [Node](https://docs.godotengine.org/en/stable/classes/class_node.html)s enter the tree (see [SceneTree docs](https://docs.godotengine.org/en/stable/tutorials/scripting/scene_tree.html)), we create corresponding RealityKit [Entity](https://developer.apple.com/documentation/realitykit/entity)s for them, so there is a "mirrored" tree. Godot [Mesh](https://docs.godotengine.org/en/stable/classes/class_mesh.html)es become RealityKit [MeshResource](https://developer.apple.com/documentation/realitykit/meshresource)s, etc.

Once a frame, we stream any changed Node transforms to RealityKit to modify their positions/rotations/scales.


![A diagram illustrating how RealityKit's and Godot's event loops have been intertwined](/img/event-loops.jpg)

## Corresponding Godot and RealityKit concepts

| Godot    | RealityKit | Role |
| -------- | ---------- | ---- |
| [Node](https://docs.godotengine.org/en/stable/classes/class_node.html)                 | [Entity](https://developer.apple.com/documentation/realitykit/entity)  | The thing that exists in a tree (has a parent, and children), that you make up your game scene with. Each of these has a position, rotation and scale that gets applied downward in the tree. |
|          | [Component](https://developer.apple.com/documentation/realitykit/component) | RealityKit has an [Entity-Component-System](https://developer.apple.com/documentation/realitykit/implementing-systems-for-entities-in-a-scene), but Godot does not. |
| [Mesh](https://docs.godotengine.org/en/stable/classes/class_mesh.html)                 | [MeshResource](https://developer.apple.com/documentation/realitykit/meshresource) | The data that makes up the triangles and textures that is an object you can render in your game. |



## Dependencies

GodotVision depends on the [SwiftGodotKit](https://github.com/migueldeicaza/SwiftGodotKit) and [SwiftGodot](https://github.com/migueldeicaza/SwiftGodot) projects.

SwiftGodotKit embeds Godot in a Swift application.

SwiftGodot provides bindings from Swift to Godot via Godot's [GDExtension](https://docs.godotengine.org/en/stable/tutorials/scripting/gdextension/what_is_gdextension.html) mechanism.