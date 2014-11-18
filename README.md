# three-orbit-viewer

[![stable](http://badges.github.io/stability-badges/dist/stable.svg)](http://github.com/badges/stability-badges)

Quick harness to create a runnable demo for ThreeJS scenes.

```js
var createOrbitViewer = require('three-orbit-viewer')(THREE)

var app = createOrbitViewer({
    clearColor: 0x000000,
    clearAlpha: 1.0,
    fov: 65,
    position: new THREE.Vector3(1, 1, -2)
})

var geo = new THREE.BoxGeometry(1,1,1)
var mat = new THREE.MeshBasicMaterial({ wireframe: true, color: 0xffffff })
var box = new THREE.Mesh(geo, mat)
app.scene.add(box)

app.on('tick', function(dt) {
    //.. handle pre-render updates    
})

app.on('ready', function() {
    //.. handle DOM ready 
})
```

## Usage

[![NPM](https://nodei.co/npm/three-orbit-viewer.png)](https://nodei.co/npm/three-orbit-viewer/)

#### `viewer = createViewer(THREE)([options])`

This module exports a function which accepts the THREE instance, and returns a new function which creates the orbit viewer with the specified options. 


- `fov` field of view, defaults to 50
- `clearColor` the THREE.Color or hex code, default black
- `clearAlpha` the alpha, default 0
- `position` THREE.Vector3 for the initial camera position, defaults to [1, 1, -2]
- `target` THREE.Vector3 for the initial orbit controller's target
- other options that could be passed into [canvas-app](https://www.npmjs.org/package/canvas-app)

#### `viewer.on('tick')`

Listens for tick events, dispatched with `dt` as the first and only parameter.

#### `viewer.on('resize')`

Listens for resize events, dispatched with `width, height` as parameters. Camera aspect, renderer viewport, and canvas retina scaling is already taken into account.

#### `viewer.renderer`

Instance of THREE.WebGLRenderer

#### `viewer.scene`

Instance of THREE.Scene

#### `viewer.camera`

Instance of THREE.PerspectiveCamera

#### `viewer.controller`

Instance of [three-orbit-controller](https://www.npmjs.org/package/three-orbit-controller).

#### `viewer.engine`

Instance of [canvas-app](https://www.npmjs.org/package/canvas-app) which you can call `stop()` and `start()` on, or access for current width/height/fps/etc.

#### Versioning

Because of ThreeJS's versioning, the safest choice is to use `--save-exact` when installing this module (no tilde or caret). The minor version should line up with major ThreeJS releases, e.g. `0.69.0` => `r69`. Please submit a PR or issue if you notice any issues going forward. 

## License

MIT, see [LICENSE.md](http://github.com/mattdesl/three-orbit-viewer/blob/master/LICENSE.md) for details.