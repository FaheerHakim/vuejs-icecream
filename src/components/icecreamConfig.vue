<script setup>
import * as THREE from 'three';
import { watch, onMounted, ref } from 'vue'
import {GLTFLoader} from 'three/examples/jsm/loaders/GLTFLoader.js';
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js';


const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );


const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth/2, window.innerHeight/2);

const controls = new OrbitControls( camera, renderer.domElement );
const canvasContainer = ref(null)

onMounted(() => {
    canvasContainer.value.appendChild(renderer.domElement)
    controls.update()
})

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
    console.log(group);
    icecream = group;

    
});
   

camera.position.z = 15;

controls.update();

const props = defineProps(['flavor', 'coneFlavor'])

const flavorColors = {
    'Chocolade': 0x5E3B1B,
    'Vanilla':   0xFFE3B5,
    'Aardbei':   0xFFADDA,
    'Moka':      0x38260D
}

// watch op de prop
watch(() => props.flavor, (newFlavor) => {
    if (!icecream) return
    const color = flavorColors[newFlavor] || 0xffffff
    icecream.traverse((child) => {
        if (child.isMesh && child.name === 'Scoop') {
            child.material.color.setHex(color)
        }
    })
})


const coneflavorColors = {
    'Chocolade': 0x4F351F,
    'Vanilla':   0xFFDEC2,
}

// watch op de prop
watch(() => props.coneFlavor, (newFlavor) => {
    if (!icecream) return
    const color = coneflavorColors[newFlavor] || 0xffffff
    icecream.traverse((child) => {
        if (child.isMesh && child.name === 'Cone') {
            child.material.color.setHex(color)
        }
    })
})


function animate() {

    if (icecream) icecream.rotation.y += 0.01;
    
	renderer.render( scene, camera );

    
}

renderer.setAnimationLoop(animate);

</script>

<template>
    <div ref="canvasContainer" style="margin-top: 20rem;"></div>
</template>