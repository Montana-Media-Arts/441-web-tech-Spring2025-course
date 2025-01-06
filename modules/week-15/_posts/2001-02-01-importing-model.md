---
title: Importing a Model
module: 15
jotted: true
---

## Importing a Scene or Model

When you add a model to a scene, you are loading it through the browser. As you likely already know, loading anything from a website is an asynchronous function. Therefore, before you can do anything with your models, you first must ensure they have been loaded successfully. You can do this using the ImportMeshAsync method of the SceneLoader, which can be done as follows:

```js
BABYLON.SceneLoader.ImportMeshAsync(model_name, folder_path, file_name, scene);
```

The scene parameter is optional and will default to the current scene. The first parameter can be any one of three types depending whether you want to load all the models, just one model or a list of models.

```js
BABYLON.SceneLoader.ImportMeshAsync("", "/relative path/", "myFile"); //Empty string loads all meshes
BABYLON.SceneLoader.ImportMeshAsync("model1", "/relative path/", "myFile"); //Name of the model loads one model
BABYLON.SceneLoader.ImportMeshAsync(["model1", "model2"], "/relative path/", "myFile"); //Array of model names
```

Note that any of the calls above will only load the models; however, you will not be able to manipulate them in any way. Internally, a Promise object is setup and returned, but the above code does nothing with the result of that Promise. Examples of this are in the following two playgrounds, which only import the named models.

<a href="https://playground.babylonjs.com/#YNEAUL#12" target="_blank">Example 1</a>

<a href="https://playground.babylonjs.com/#YNEAUL#11" target="_blank">Example 2</a>

Therefore, in order to act on the result and manipulate the objects, we follow the Promise with the then method to call a function with the result of the Promise. The result is an object containing, among other things, the property meshes which contains all the loaded models. We can use this array, or their names, to manipulate each mesh.

```js
BABYLON.SceneLoader.ImportMeshAsync("", "/relative path/", "myFile").then((result) => {
    result.meshes[1].position.x = 20;
    const myMesh1 = scene.getMeshByName("myMesh_1");
    myMesh1.rotation.y = Math.PI / 2;
});
```

### Moving On
Having a working scene in the playground is one thing, but you will ultimately want your game or application to run on your own website. In the next section, we will provide an HTML template to do just this.

### Warning
An obvious statement - different file types export models differently.

A less obvious statement - different file types may be changed when importing into Babylon.js.

You need to be aware of how the type you are using affects the outcome. It is not appropriate at this stage to go into detail but the following examples indicate why this is important.

Some software saves all meshes with a rotationQuaternion set and you cannot then use the rotation methods unless you first add:

```js
myMesh.rotationQuaternion = null; //Any version of Babylon.js
```

```js
myMesh.rotation = BABYLON.Vector3.Zero(); //babylon.js versions > 4.00
```




