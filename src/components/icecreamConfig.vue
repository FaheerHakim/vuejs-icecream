<script setup>
import * as THREE from 'three';
import {GLTFLoader} from 'three/examples/jsm/loaders/GLTFLoader.js';
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js';



const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );


const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth/2, window.innerHeight/2);
document.body.appendChild( renderer.domElement );

renderer.setClearColor(0x000000, 0);

const light = new THREE.AmbientLight(0xffffff, 1);
scene.add(light);

const directionalLight = new THREE.DirectionalLight(0xffffff, 0.5);
directionalLight.position.x = 1;
directionalLight.position.z = 1;
scene.add(directionalLight);



let icecream;

const gltfLoader = new GLTFLoader();

gltfLoader.load('../../models/icecream.glb', (gltf) => {
    
    const mesh = gltf.scene;
    
    mesh.scale.set(0.08, 0.08, 0.08);

    const box = new THREE.Box3().setFromObject(mesh);

    const center = box.getCenter(new THREE.Vector3());

    mesh.position.sub(center);

    const group = new THREE.Group();

    group.add(mesh);

    scene.add(group);

    icecream = group;
});

camera.position.z = 15;

function animate() {

    if (icecream) icecream.rotation.y += 0.01;

	renderer.render( scene, camera );

}

renderer.setAnimationLoop(animate);
</script>