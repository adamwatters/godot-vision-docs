---
slug: /
title: About
---

# GodotVision

---

## Introduction

With **GodotVision**, you can create games and apps for Apple's [**visionOS**](https://developer.apple.com/documentation/visionos) using the [**Godot Game Engine**](https://godotengine.org/).

[![a short gif of a visionOS game](/img/cow_castle.gif)](https://apps.apple.com/us/app/defend-cow-castle/id6476968953)
_[Defend Cow Castle](https://apps.apple.com/us/app/defend-cow-castle/id6476968953), a visionOS game made with GodotVision_

GodotVision runs a [headless Godot](https://github.com/godotengine/godot/blob/a7b860250f305f6cbaf61c30f232ff3bbdfdda0b/main/main.cpp#L1284) instance that controls native [RealityKit views](https://developer.apple.com/documentation/realitykit/realityview/). Roughly speaking: Godot is the backend, RealityKit is the frontend.

You get the power of the Godot editor AND the awesome native rendering features of visionOS, e.g. [image-based-lighting](https://developer.apple.com/videos/play/wwdc2023/10095/?time=114) and foveated rendering.

Currently, GodotVision supports rendering to [visionOS Volumes](https://developer.apple.com/videos/play/wwdc2023/10260/?time=127), and connects native spatial gestures to events in Godot.

In the future, GodotVision will support [ARKit features including hand tracking and plane detection](https://developer.apple.com/documentation/arkit/arkit_in_visionos).

---

## Why use a game engine for visionOS dev?

SwiftUI and RealityKit might be all you need!

But, if you're building something with lots of moving parts, a game engine can help you manage complex scenes and avoid reimplementing common game systems.

Consider an adventure game. The game features a map composed of tiles, and a camera that pans from tile to tile to follow the character. And enemy monsters who navigate around obstacles to attack your character. And an inventory and health system. And...

**A game engine will definitely make this easier!**

![an animated GIF of the original Legend of Zelda for the NES](/img/zelda.gif)

<small>
*Yes, The Legend of Zelda was coded in assembly.
</small>

---

## Why Godot?

GodotVision is similair to [Unity Polyspatial](https://developer.apple.com/videos/play/wwdc2023/10088/?time=134) in both its goals and approach.

We chose to build on Godot for a few reasons.

1. Godot is fun and we like it.
2. Godot is rapidly improving, and the community around it is growing.
3. Godot is [Free and Open Source](https://godotengine.org/license/)

---
