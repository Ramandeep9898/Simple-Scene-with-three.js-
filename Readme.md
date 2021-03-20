# **FIRST-SCENE** :

## **4 Elements To start with** :

1.  A Scene that will Contain the Objects.
1.  Some Objects.
1.  A Camera.
1.  A Renderer.

## **1. A Scene** :

1. It's like a container.
1. We put Objects, Lights, Models etc in it.
1. At some point we say three.js to renderer at that point.

```javaScript
const scene = new THREE.Scene();
```

## **2. Objects** :

Can be Many things.

1. Primitive Geometries.
1. Imported Models.
1. Particles.
1. etc.

let's start with simple red cude.

> We need to create a [Mesh](https://threejs.org/docs/index.html?q=mesh#api/en/objects/Mesh)
> Conbination of **GEOMETRY** (Shape) and **MATERIAL** (HOW IT LOOKS)
> Start with a [**BoxGeometry**](https://threejs.org/docs/index.html?q=box#api/en/geometries/BoxGeometry) and [**MeshBasicMaterial**](https://threejs.org/docs/index.html?q=mesh#api/en/materials/MeshBasicMaterial)

## GEOMETRY

Instantiate a [**BoxGeometry**](https://threejs.org/docs/index.html?q=box#api/en/geometries/BoxGeometry)

```javaScript
const geometry = new THREE.BoxGeometry(1, 1, 1);
```

the three parametes corresponds to the the box's size.

## MATERIAL

Instantiate a [**MeshBasicMaterial**](https://threejs.org/docs/index.html?q=mesh#api/en/materials/MeshBasicMaterial)

```javascript
const material = new THREE.MeshBasicMaterial({ color: "red" });
```

## MESH

Don't forget to add to the mesh.

```JAVASCRIPT
const mesh = new THREE.Mesh(geometry, material);
scene.add(mesh);
```

## **3. Camera** :

1. Not visible
1. serve as point of veiw when doing a render
1. can have multiple and switch between then
1. different types.
1. We are going to use [prespectiveCamera]()

```javascript
const camera = new THREE.PerspectiveCamera(...);
scene.add(camera);
```

## Two essential parameters.

### **1. The Field of veiw.**

Vertical vision angle(in deg).also called fov.

```javascript
const camera = new THREE.PerspectiveCamera(75, ...);
scene.add(camera);
```

### **2. The Aspect Ratio**

The width of the render divided by the height of the rebder . <br>
We don't have a render yet, but we can decide on a size now. <br>
Create a sizes object containing temp values.

```javascript
const sizes = {
  width: 800,
  height: 600,
};

// Camera
const camera = new THREE.PerspectiveCamera(75, sizes.width / sizes.height);
camera.position.z = 2;
scene.add(camera);
```

## **4. Render **

1. Render the scene from the camera point of veiw .
1. result drawn into a canvas .

Use document.querySelector(...) to retrive the canvas we created in the HTML and store it in a canvas variable .
update the size of the renderer.
CALL render(... ) METHOD ON THE RENDERER WITH scene AND THE camera as parameters

```javascript
const canvas = document.querySelector(".WebGL");
const renderer = new THREE.WebGLRenderer({
  canvas: canvas,
});
renderer.setSize(sizes.width, sizes.height);
renderer.render(scene, camera);
```
