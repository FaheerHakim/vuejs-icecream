<script setup>
import * as THREE from 'three';
import {GLTFLoader} from 'three/examples/jsm/loaders/GLTFLoader.js';



const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );

const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth/2, window.innerHeight/2);
document.body.appendChild( renderer.domElement );

let icecream;
const gltfLoader = new GLTFLoader();

gltfLoader.load('../../models/icecream.glb', (gltf) => {
    icecream = gltf.scene;
    console.log(gltf);
    scene.add(gltf.scene);
});

camera.position.z = 15;

function animate() {

    renderer.render(scene, camera);

}

animate();
</script>