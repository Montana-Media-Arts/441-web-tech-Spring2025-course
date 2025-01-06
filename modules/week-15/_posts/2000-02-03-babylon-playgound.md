---
title: Babylon Playground
module: 15
jotted: true
---

## Babylon Playground

Welcome to "The Very First Step." This document is designed for absolutely EVERYONE. Whether you're an expert web developer diving into 3D, an amazing artist wanting to create 3D experiences on the web, a student/tinkerer curious about programming, or an absolute beginner, this is your very first step to learning Babylon. We strongly encourage everyone new to Babylon to go through this doc before going any further through the docs.

This doc will take you on a VERY brief journey of creating and hosting your very first Babylon.js Web Experience. You'll learn about the Babylon.js playground, scratch the surface of learning the core engine, and save your work as a ready-to-host .html file.

### The Babylon.js Playground

The single most important tool available to you as you learn and develop with Babylon, is the Babylon.js Playground.

The playground is your toybox, your tinker environment, your laboratory. This simple website allows you to write Babylon code on the left, and see instant updates on the right. It's really that simple.

The playground is CRITICAL to your learning journey for two reasons:

1. An amazing cycle of code --> see updates instantly. Learn by doing!
2. It's saveable & shareable!

Why is saveable & shareable important for learning? Through your Babylon journey, you will undoubtedly come across something that you could use some help figuring out. It is important that you have a safe and welcoming space to ask for help! This is why the core dev team staffs the Babylon.js Forum every weekday, so we can be there alongside you to help you learn.

And when it comes time to help you learn or solve a problem, we need to SEE and UNDERSTAND the context behind the problem. Sharing your saved playgrounds is the PERFECT solution and is mandatory on the forum. When you're stuck, save your playground, head to the forum, reach out for help, and share the playground. We think you'll be pleasantly surprised at how quickly you'll get help by following this process.

So now that you know the playground is the single most important tool to start learning, let's open it up in a new tab.

[Babylon Playground](https://playground.babylonjs.com/)

### Your First Creation

Welcome to the Playground! Using the playground is as simple as modifying/creating code in the code editor on the left, and seeing updates in the live Babylon scene on the right! You'll also see a default Babylon scene that we've set up for you. Take a quick look at the comments in green font in the code editor. These comments should give you a basic idea of what's happening with each line of code that's written. Pretty simple right?

There's no better way to start learning than by doing, so let's make our first scene update!

On lines 20-24 you see the following lines of code:

```js
// Our built-in 'sphere' shape.
var sphere = BABYLON.MeshBuilder.CreateSphere("sphere", { diameter: 2, segments: 32 }, scene);

// Move the sphere upward 1/2 its height
sphere.position.y = 1;
```
Go ahead and highlight those lines of code and hit DELETE! You've just made your first change! Feel good? But wait, nothing happened in the scene? That's because we have to re-run the scene with our changes. You can do that by either pressing ALT+ENTER on your keyboard or pressing the 'run' button in the UI.

Quick side note - Throughout this document we'll add links to playgrounds showing you exactly what changes were just made. You can reference these playgrounds with your own progress if you ever get stuck. The little arrow symbol will open these playgrounds in a new tab.

Let's make another change!

Find the line of code that creates the ground plane and add these new lines underneath it:

```js
const groundMaterial = new BABYLON.StandardMaterial("Ground Material", scene);
groundMaterial.diffuseColor = BABYLON.Color3.Red();
ground.material = groundMaterial;
```

Congratulations! You just created a new material, assigned that new material to the ground plane, and assigned it's diffuse channel to be the color red! Pretty cool huh?! Don't worry if some of that is still a bit confusing, the takeaway here is that you're making code changes on the left and seeing updates on the right.

Ok time for another change.

Find this line:

```js
groundMaterial.diffuseColor = BABYLON.Color3.Red();
```

Replace it with these two lines and run the scene again:

```js
let groundTexture = new BABYLON.Texture(Assets.textures.checkerboard_basecolor_png.rootUrl, scene);
groundMaterial.diffuseTexture = groundTexture;
```

Pretty cool! You've now created your first Babylon.js texture and assigned it to the texture property of your ground material!

Ok it's time for another addition to the scene. After all of your ground-related code, give yourself a little space by hitting enter and on a new line press CTRL+SPACE. This will spawn a list of playground templates. These templates are handy pieces of code that you will likely reuse over and over again through your Babylon learning journey. Go ahead and select the template that says "Import a Mesh w/Callback".

You should see the following lines of code pop right into the playground:

```js
BABYLON.SceneLoader.ImportMesh("meshName", "url to the mesh parent directory", "Mesh filename.fileextension", scene, function (newMeshes) {});

```

Let's do a few more things:

1. Delete the word 'meshName' but leave the quotes "".
2. Replace "url to the mesh parent directory" (including quotes) with this:

```js
Assets.meshes.Yeti.rootUrl;
```

3. Replace the "Mesh filename.fileextension" (including quotes) with this:

```js
Assets.meshes.Yeti.filename;
```

4. After the BABYLON.SceneLoader.ImportMesh line, but before the "});" add the following line:

```js
newMeshes[0].scaling = new BABYLON.Vector3(0.1, 0.1, 0.1);
```

5. Run the scene

Whoa! Cool! You just added an animated .gltf object into the scene! And you also scaled it down to fit on the groundplane! Well done!

Let's change one final thing. We want our scene to be interactive, after all isn't that what why you're here - to create interactive web experiences?

Delete lines 5-9.

Press CTRL+SPACE to bring up the playground templates and create an Arc Rotate Camera.

Run the scene and click+drag or touch+drag on the Babylon scene.

WooHoo! You've added interaction to the scene! Great job! Go ahead and save your playground by pressing CTRL+S or hitting the save button.

The .html File
At this point, let's say we're happy with our creation, and we want to put the Babylon scene (without the code editor and UI) out into the world for everyone to play with.

Getting your Babylon scene ready to host is as simple as pressing a button. Either press SHIFT+CTRL+S or press the Download button to download an .html file of your Babylon scene to your system.

That's it! You've got everything you need for the world to see your first Babylon experience! Now all we need to do is host it somewhere for the world to see it!

### Hosting Your Babylon Project
Remember you can put your pages on GitHub pages to host it.




