---
title: Setting the App
module: 15
jotted: true
---

## Setting up your first app

 You will have seen that the template needed for any code on the Playground is:

 ```js
 var createScene = function () {
  var scene = new BABYLON.Scene(engine);

  // Add a camera to the scene and attach it to the canvas
  // Add a lights to the scene

  //Your Code

  return scene;
};
```

By following this format in you own project you can quickly drop it into your own HTML page using the following as a template.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>Babylon Template</title>

    <style>
      html,
      body {
        overflow: hidden;
        width: 100%;
        height: 100%;
        margin: 0;
        padding: 0;
      }

      #renderCanvas {
        width: 100%;
        height: 100%;
        touch-action: none;
      }
    </style>

    <script src="https://cdn.babylonjs.com/babylon.js"></script>
    <script src="https://cdn.babylonjs.com/loaders/babylonjs.loaders.min.js"></script>
    <script src="https://code.jquery.com/pep/0.4.3/pep.js"></script>
  </head>

  <body>
    <canvas id="renderCanvas" touch-action="none"></canvas>
    <!-- touch-action="none" for best results from PEP -->

    <script>
      var createScene = function () {
        // This creates a basic Babylon Scene object (non-mesh)
        var scene = new BABYLON.Scene(engine);

        // This creates and positions a free camera (non-mesh)
        var camera = new BABYLON.FreeCamera(
          "camera1",
          new BABYLON.Vector3(0, 5, -10),
          scene
        );

        // This targets the camera to scene origin
        camera.setTarget(BABYLON.Vector3.Zero());

        // This attaches the camera to the canvas
        camera.attachControl(canvas, true);

        // This creates a light, aiming 0,1,0 - to the sky (non-mesh)
        var light = new BABYLON.HemisphericLight(
          "light",
          new BABYLON.Vector3(0, 1, 0),
          scene
        );

        // Default intensity is 1. Let's dim the light a small amount
        light.intensity = 0.7;

        // Our built-in 'sphere' shape.
        var sphere = BABYLON.MeshBuilder.CreateSphere(
          "sphere",
          { diameter: 2, segments: 32 },
          scene
        );

        // Move the sphere upward 1/2 its height
        sphere.position.y = 1;

        // Our built-in 'ground' shape.
        var ground = BABYLON.MeshBuilder.CreateGround(
          "ground",
          { width: 6, height: 6 },
          scene
        );

        return scene;
      };
      const canvas = document.getElementById("renderCanvas"); // Get the canvas element
      const engine = new BABYLON.Engine(canvas, true); // Generate the BABYLON 3D engine

      // Add your code here matching the playground format

      const scene = createScene(); //Call the createScene function

      // Register a render loop to repeatedly render the scene
      engine.runRenderLoop(function () {
        scene.render();
      });

      // Watch for browser/canvas resize events
      window.addEventListener("resize", function () {
        engine.resize();
      });
    </script>
  </body>
</html>

```

This line

```html
<script src="https://cdn.babylonjs.com/loaders/babylonjs.loaders.min.js"></script>
```

allows you to import models into your scene.

This line

```html
<script src="https://code.jquery.com/pep/0.4.3/pep.js"></script>
```

allows you to use a touch screen.


### Import a Model Setup

The following loads a box model into an app.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>Babylon Template</title>

    <style>
      html,
      body {
        overflow: hidden;
        width: 100%;
        height: 100%;
        margin: 0;
        padding: 0;
      }

      #renderCanvas {
        width: 100%;
        height: 100%;
        touch-action: none;
      }
    </style>

    <script src="https://cdn.babylonjs.com/babylon.js"></script>
    <script src="https://cdn.babylonjs.com/loaders/babylonjs.loaders.min.js"></script>
    <script src="https://code.jquery.com/pep/0.4.3/pep.js"></script>
  </head>

  <body>
    <canvas id="renderCanvas" touch-action="none"></canvas>
    <!-- touch-action="none" for best results from PEP -->

    <script>
      const canvas = document.getElementById("renderCanvas"); // Get the canvas element
      const engine = new BABYLON.Engine(canvas, true); // Generate the BABYLON 3D engine

      // Add your code here matching the playground format
      const createScene = function () {
        const scene = new BABYLON.Scene(engine);

        BABYLON.SceneLoader.ImportMeshAsync("", "https://assets.babylonjs.com/meshes/", "box.babylon");

        const camera = new BABYLON.ArcRotateCamera("camera", -Math.PI / 2, Math.PI / 2.5, 15, new BABYLON.Vector3(0, 0, 0));
        camera.attachControl(canvas, true);
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));

        return scene;
      };

      const scene = createScene(); //Call the createScene function

      // Register a render loop to repeatedly render the scene
      engine.runRenderLoop(function () {
        scene.render();
      });

      // Watch for browser/canvas resize events
      window.addEventListener("resize", function () {
        engine.resize();
      });
    </script>
  </body>
</html>
```

### Code a Model Setup

The following creates a box model in an app.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>Babylon Template</title>

    <style>
      html,
      body {
        overflow: hidden;
        width: 100%;
        height: 100%;
        margin: 0;
        padding: 0;
      }

      #renderCanvas {
        width: 100%;
        height: 100%;
        touch-action: none;
      }
    </style>

    <script src="https://cdn.babylonjs.com/babylon.js"></script>
    <script src="https://cdn.babylonjs.com/loaders/babylonjs.loaders.min.js"></script>
    <script src="https://code.jquery.com/pep/0.4.3/pep.js"></script>
  </head>

  <body>
    <canvas id="renderCanvas" touch-action="none"></canvas>
    <!-- touch-action="none" for best results from PEP -->

    <script>
      const canvas = document.getElementById("renderCanvas"); // Get the canvas element
      const engine = new BABYLON.Engine(canvas, true); // Generate the BABYLON 3D engine

      // Add your code here matching the playground format
      const createScene = function () {
        const scene = new BABYLON.Scene(engine);

        BABYLON.MeshBuilder.CreateBox("box", {});

        const camera = new BABYLON.ArcRotateCamera("camera", -Math.PI / 2, Math.PI / 2.5, 15, new BABYLON.Vector3(0, 0, 0));
        camera.attachControl(canvas, true);
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));

        return scene;
      };

      const scene = createScene(); //Call the createScene function

      // Register a render loop to repeatedly render the scene
      engine.runRenderLoop(function () {
        scene.render();
      });

      // Watch for browser/canvas resize events
      window.addEventListener("resize", function () {
        engine.resize();
      });
    </script>
  </body>
</html>
```

Okay this gets you started.  If you would like to continue exploring, please feel free to navigate here:

<a href="https://doc.babylonjs.com/features/introductionToFeatures/chap2" target="_blank">Chapter 2</a>