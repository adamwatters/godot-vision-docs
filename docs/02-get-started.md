---
slug: /get-started
title: Get Started
---

# Get Started

---

## Objective

A sample GodotVision project up and running. You can use it as a starting point to build your app or game.

---

## Requirements

What you'll need:

- [Godot 4](https://godotengine.org/download/macos/)
- [XCode 15](https://developer.apple.com/xcode/)

---

## Download GodotVisionExample

Get started by downloading or cloning the [starter project](https://github.com/kevinw/GodotVisionExample)

```bash
git clone git@github.com:kevinw/GodotVisionExample.git
```

Here's what you should find inside:

```
GodotVisionExample		LICENSE
GodotVisionExample.xcodeproj	README.md
Godot_Project			docs
```

`GodotVisionExample` is the native Xcode project, and `Godot_Project` is, well, the Godot project.

---

## 🚨 Important - Open in Godot First

Before we run the project on visionOS, we need to Godot to automatically import assets. To make that happen, we open the project in Godot.

Launch Godot and select `Import` in the Project Manager.

![godot project manager ui](/img/ss_1.png)

Navigate to `GodotVisionExample/Godot_Project` and select `project.godot`

![godot import select file ui](/img/ss_2.png)

Select `Import & Edit`

![godot confirm project path ui](/img/ss_3.png)

You should see the sample scene. Hit the play button to run it.

![godot scene editor with sample scene loaded](/img/ss_4.png)

If everything worked correctly, you'll see the scene running.

![sample scene running in godot play mode](/img/ss_5.png)

---

## Run the Xcode Project

Open `GodotVisionExample/GodotVisionExample.xcodeproj` in Xcode.

![Xcode open project ui](/img/ss_6.png)

:::warning
If you encounter issues in this section of the guide - please let us know in the [GodotVision Discord](https://discord.gg/AWJvFKaeW8)!

We think there are a few dialogue boxes to contend with on the first install.

Bonus points if you capture screenshots.
:::

When you first open the project, Xcode should download and install a few Swift Packages, including GodotVision.

![swift package dependencies](/img/ss_7.png)

That should be it! Select your device or simulator, and hit play.

![Xcode select device and build](/img/ss_8.png)

If everything is working, you should see the example scene running on visionOS. You can drag one block and tap the other to play a sound. You should also see a small panel at the bottom front of the panel that allows you to switch between the other example scenes in the project.

![a gif of the example project running on visionOS](/img/example.gif)

---

## Make an Update

To make changes to the project, update the scene in Godot and rebuild in Xcode.

Try changing the text mesh and its material to see how it works.

![visionOS screenshot of the example project with the text updated to You Are Awesome](/img/ss_9.jpeg)

---

## Optional: Clone GodotVision

GodotVision is setup as a [Xcode package dependency](https://developer.apple.com/documentation/xcode/adding-package-dependencies-to-your-app) in the GodotVisionExample project. This means that by default you cannot make changes to GodotVision itself.

Since it's under active development, you may want to add features or make changes to the way it works for your project. You can accomplish this easily by setting up a "local project" override in Xcode:

1. Clone the [GodotVision](https://github.com/kevinw/GodotVision) repository next to your project.
2. In Finder, drag the GodotVision folder onto your Xcode project's navigator/file tree on the left. This establishes a ["local project package dependency"](https://developer.apple.com/documentation/xcode/editing-a-package-dependency-as-a-local-package) override, and changes to GodotVision will have immediate effect in your project.

<video controls>
  <source src="/img/local-override.mp4" type="video/mp4"></source>
</video>

---

## Next Steps

**Congrats! You're on your way to building visionOS apps with Godot.**

Now, choose your own adventure:

If you're new to Godot and want to invest a couple hours building your foundation, we recommend the [3D game tutorial](https://docs.godotengine.org/en/stable/getting_started/first_3d_game/index.html) in the official Godot docs.

If you're ready to start building for visionOS, the [**Guides**](/guides) section ahead contains documentation on GodotVision specific concepts.
