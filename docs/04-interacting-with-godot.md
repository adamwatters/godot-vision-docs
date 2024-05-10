---
slug: /interacting-with-godot
title: Interacting with Godot
---

# Interacting with Godot

## SwiftGodot

An imporant concept to understand: GodotVision uses the [SwiftGodot](https://migueldeicaza.github.io/SwiftGodotDocs/documentation/swiftgodot/) library and your app has access to all of SwiftGodot's functionality via a simple `import SwiftGodot` in your codebase. This means you can, for example manipulate `Node`s, call any functions, emit signals, change properties, and more.

## Example: calling a `gdscript` method from Swift

From `GodotVisionCoordinator` you can get the active [SceneTree](https://docs.godotengine.org/en/stable/classes/class_scenetree.html) via its `sceneTree` property. From the `SceneTree` you can get its `root` `Node`. On a `Node` you can use the [findChild method](https://docs.godotengine.org/en/stable/classes/class_node.html#class-node-method-find-child) with a `recursive: true` argument to find a specific `Node` in your scene hierarchy.

```swift
func triggerGodotFunction(godotVision: GodotVisionCoordinator) {
    guard let rootNode = godotVision.sceneTree?.root else {
        print("No root node.")
        return
    }

    guard let playerRootNode = rootNode.findChild(pattern: "PlayerRoot", recursive: true) else {
        print("Could not find node named 'PlayerRoot')
        return
    }

    playerRootNode.call(method: "reset", arguments: 1) // TODO

}