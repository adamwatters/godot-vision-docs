---
slug: /guides/metadata
title: Metadata
---

# Metadata

GodotVision recognizes specific metadata on your Nodes to pass additional information to RealityKit.

![A screenshot of a Godot inspector window, with the mouse cursor over the "Add Metadata" button](/img/inspector_metadata.jpg)

## Recognized Metadata

### `hover_effect` (bool)

Default value: `false`

If true, the RealityKit Entity for your Node will be given the [HoverEffectComponent](https://developer.apple.com/documentation/realitykit/hovereffectcomponent), which gives it a subtle visual highlight when the user's gaze is on it.

This requires `input_ray_pickable` in [`CollisionObject3D`](https://docs.godotengine.org/en/stable/classes/class_collisionobject3d.html) to be true, so that your Entity also gets a [`CollisionComponent`](https://developer.apple.com/documentation/realitykit/collisioncomponent).

### `grounding_shadow` (bool)

Default value: `true`

If you don't want a mesh to get a [GroundingShadowComponent](https://developer.apple.com/documentation/realitykit/groundingshadowcomponent), set this to `false`.
