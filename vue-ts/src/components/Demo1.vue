<template>
    <!-- <div id="demo1" style="width: 800px; height: 800px;"></div> -->
    <canvas id="demo1" width="800" height="800"></canvas>
</template>
<script setup lang="ts">
import { onMounted } from 'vue'
import * as THREE from 'three'

defineProps<{ msg: string }>()

//const message = ref("test")

const buildScence = () => {
    const canvas = document.getElementById('demo1') as  HTMLCanvasElement;
    const scene = new THREE.Scene()
    const camera = new THREE.PerspectiveCamera(45, 800 / 800, 1, 500)
    camera.position.set(0, 0, 100);
    camera.lookAt(0, 0, 0);
    const renderer = new THREE.WebGLRenderer({ canvas });
    const points = [];
    points.push(new THREE.Vector3(- 10, 0, 0));
    points.push(new THREE.Vector3(0, 10, 0));
    points.push(new THREE.Vector3(10, 0, 0));
    const geometry = new THREE.BufferGeometry().setFromPoints( points );
    const material = new THREE.LineBasicMaterial( { color: 0x0000ff } );
    const line = new THREE.Line( geometry, material );
    scene.add(line);
    renderer.render( scene, camera );
}

onMounted(() => {
    buildScence()
})

</script>