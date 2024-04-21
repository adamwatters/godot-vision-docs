---
slug: /guides/gestures
title: Input & Spatial Gestures
---


# Gestures and Input

You can easily let players pinch and drag objects in the world. 

## Receiving Taps

To receive taps (gaze + a pinch in VisionOS) you do exactly the same thing you do in Godot to receive a mouse click on a Node--you set the [`input_ray_pickable`](https://docs.godotengine.org/en/stable/classes/class_collisionobject3d.html#class-collisionobject3d-property-input-ray-pickable) property of your `CollisionObject3D` to true. 

<img alt="an image showing the 'input_ray_pickable' property on a CollisionObject3D" src="/img/input_ray_pickable.jpg"></img>

And then connect the `input_event` signal to some code that responds to a `InputEventMouseButton`:

<img alt="an image showing an input_event signal connection" src="/img/input_event_signal.jpg"></img>

That signal needs to connect to a function in a gdscript. An example script might look like:

```
extends StaticBody3D

func _on_input_event(_camera, event, _position, _normal, _shape_idx):
    if event is InputEventMouseButton:
        if event.pressed:
            print("TAPPED ON ", self)
```


:::info[Under the hood]

<details>
  <summary>
    How taps map to RealityKit
  </summary>
    <p>GodotVision sees `CollisionObject3D`s with `input_ray_pickable` and adds an [`InputTargetComponent`](https://developer.apple.com/documentation/RealityKit/InputTargetComponent) to its corresponding Entity.</p>
    <p>You can also get a [`HoverEffectComponent`](https://developer.apple.com/documentation/realitykit/hovereffectcomponent) with metadata `hover_effect`--see [Metadata](/guides/metadata#hover_effect-bool) for more info.</p>

</details>

:::

## Special Custom Signals

### `spatial_drag` signal

Any `CollisionObject3D` with a [custom signal](https://docs.godotengine.org/en/stable/getting_started/step_by_step/signals.html#custom-signals) named `spatial_drag` will receive drag gesture events from GodotVision. The signal gets called with a Dictionary with the following parameters:

```
{
    "phase": String,                       // "began", "changed", or "ended"
    "global_transform": Transform3D,       // the current Transform3D of the Node
    "start_global_transform": Transform3D, // the Transform3D of the Node when the gesture began
}
```

#### Example Drag Script

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
