# Prompt-Powered Kickstart: Building a Beginner’s Toolkit for Three.js

## 1. Title & Objective

**Project Title:** Prompt-Powered Kickstart: Getting Started with Three.js (Frontend Only)

**Chosen Technology:** Three.js

**Why Three.js?**
Three.js makes it possible to create rich 3D experiences directly in the browser using JavaScript and WebGL, without needing deep graphics programming knowledge. I chose Three.js because it bridges creativity and engineering, and it is increasingly used in modern web apps, data visualization, games, and virtual galleries.

**End Goal:**
To build a simple frontend-only web application that renders a rotating 3D cube in the browser using Three.js.

---

## 2. Quick Summary of the Technology

**What is Three.js?**
Three.js is a JavaScript library that simplifies working with WebGL to create and display animated 3D graphics in the browser.

**Where is it used?**

* Interactive websites
* Data visualization dashboards
* Games and simulations
* Virtual tours and art galleries

**Real-world example:**
Nike and other brands use Three.js-powered 3D product previews on their websites to allow users to interact with products in real time.

---

## 3. System Requirements

* **OS:** Linux / macOS / Windows
* **Browser:** Chrome / Firefox (WebGL enabled)
* **Editor:** VS Code (recommended)
* **Tools:** None required beyond a browser (optional: VS Code Live Server extension)
* **Package Manager:** Not required (CDN-based setup)

---

## 4. Installation & Setup Instructions

This project runs entirely on the frontend using a CDN.

### Step 1: Create Project Files

Create a new folder and add the following files:

```
threejs-starter/
├── index.html
└── main.js
```

### Step 2: Add Three.js via CDN

In `index.html`, include Three.js from a CDN.

---

## 5. Minimal Working Example

### What the Example Does

* Creates a 3D scene
* Adds a camera and renderer
* Renders a rotating cube on the screen

### `index.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Three.js Starter</title>
  <style>
    body { margin: 0; overflow: hidden; }
  </style>
</head>
<body>
  <script src="https://unpkg.com/three@0.158.0/build/three.min.js"></script>
  <script src="main.js"></script>
</body>
</html>
```

### `main.js`

```javascript
// Create the scene
const scene = new THREE.Scene();

// Create a camera
const camera = new THREE.PerspectiveCamera(
  75,
  window.innerWidth / window.innerHeight,
  0.1,
  1000
);

// Create the renderer
const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

// Create a cube
const geometry = new THREE.BoxGeometry();
const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
const cube = new THREE.Mesh(geometry, material);
scene.add(cube);

// Position the camera
camera.position.z = 5;

// Animation loop
function animate() {
  requestAnimationFrame(animate);
  cube.rotation.x += 0.01;
  cube.rotation.y += 0.01;
  renderer.render(scene, camera);
}

animate();
```

### Expected Output

A green 3D cube rotating continuously in the browser window.

---

## 5b. Advanced Example: Physics-Based Vehicle Controller

The project also includes an advanced demo (`index.html`) featuring a drivable car using the Rapier physics engine.

### What the Example Does

* Creates a 3D scene with a ground plane and lighting
* Initializes the Rapier physics engine for realistic physics simulation
* Renders a controllable car with chassis and four wheels
* Implements vehicle controls using keyboard input

### Controls

* **W / Arrow Up** - Accelerate forward
* **S / Arrow Down** - Reverse
* **A / Arrow Left** - Steer left
* **D / Arrow Right** - Steer right
* **Space** - Brake
* **R** - Reset car position

### Key Technologies

* **Three.js** - 3D rendering
* **Rapier Physics** - Physics simulation via `RapierPhysics.js` addon
* **OrbitControls** - Camera controls that follow the vehicle

### Running the Demo

Open `index.html` in a browser using a local server (e.g., VS Code Live Server).

---

## 6. AI Prompt Journal

### Prompt 1

**Prompt Used:**
"Explain Three.js in simple terms and give me a minimal example that runs in the browser."

**Curriculum Link:**
Moringa GenAI Curriculum – Prompt-Based Learning

**Response Summary:**
The AI explained core Three.js concepts such as scene, camera, renderer, and mesh, and provided a minimal cube example.

**Useful Excerpt:**
"Every Three.js app needs a scene, a camera, and a renderer. Objects like cubes are meshes made from geometry and material."

**Evaluation:**
Very helpful for understanding the mental model of Three.js before writing code.

---

### Prompt 2

**Prompt Used:**
"Create a frontend-only Three.js hello world example using CDN, no build tools."

**Response Summary:**
The AI generated a simple HTML + JS setup that runs directly in the browser.

**Evaluation:**
Saved setup time and avoided unnecessary tooling for a beginner project.

---

## 7. Common Issues & Fixes

### Issue 1: Blank Screen

**Cause:** Camera not positioned correctly or object outside view.

**Fix:** Ensure `camera.position.z` is set (e.g., `camera.position.z = 5`).

---

### Issue 2: WebGL Not Supported

**Cause:** Browser or GPU does not support WebGL.

**Fix:**

* Update browser
* Enable hardware acceleration
* Test in Chrome or Firefox

---

### Issue 3: Stretched or Blurry Canvas

**Fix:**
Update renderer size on window resize:

```javascript
window.addEventListener('resize', () => {
  renderer.setSize(window.innerWidth, window.innerHeight);
  camera.aspect = window.innerWidth / window.innerHeight;
  camera.updateProjectionMatrix();
});
```

---

## 8. References

* Three.js Official Documentation: [https://threejs.org/docs/](https://threejs.org/docs/)
* Three.js Examples: [https://threejs.org/examples/](https://threejs.org/examples/)
* Discover Three.js (Book): [https://discoverthreejs.com/](https://discoverthreejs.com/)
* MDN WebGL Guide: [https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)

---

## 9. Conclusion

This beginner toolkit demonstrates how Three.js can be used to create interactive 3D content using only frontend technologies. By leveraging AI prompts, I was able to quickly understand core concepts, scaffold a working example, and troubleshoot common issues efficiently.
