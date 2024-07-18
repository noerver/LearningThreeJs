<template>
    <!-- <div id="demo1" style="width: 800px; height: 800px;"></div> -->
    <canvas id="demo1" width="800" height="800"></canvas>
</template>
<script setup lang="ts">
import { onMounted } from 'vue'
import * as THREE from 'three'
import { color, PI } from 'three/examples/jsm/nodes/Nodes.js';

defineProps<{ msg: string }>()

//const message = ref("test")

const buildScence = () => {
    const canvas = document.getElementById('demo1') as  HTMLCanvasElement;
    const scene = new THREE.Scene()
    const camera = new THREE.PerspectiveCamera(45, 800 / 800, 1, 500);

    const ambientLight = new THREE.AmbientLight(0xFFFFFF, 15)
    scene.add(ambientLight);
    const directLight = new THREE.DirectionalLight(0xff0000,1.0);
    directLight.position.set(200,5,300);
    scene.add(directLight);


    camera.position.set(0, 0, 100);
    camera.lookAt(0, 0, 0);
    const renderer = new THREE.WebGLRenderer({ canvas });
    //renderer.setClearColor(0XFFFFFF, 1.0)
    const points = [];
    points.push(new THREE.Vector3(- 10, 0, 0));
    points.push(new THREE.Vector3(0, 10, 0));
    points.push(new THREE.Vector3(10, 0, 0));

    //创建长方体
    const changGeoMetry = new THREE.BoxGeometry(5, 5, 5)
    const changMaterial = new THREE.MeshBasicMaterial( { color: 0xAADDff } );

    const cube =  new THREE.Mesh(changGeoMetry, changMaterial);

    //使用新的边框物体来设置长方体边线的颜色
    const changLineEdgesGeometry = new THREE.EdgesGeometry(changGeoMetry);
    const changLineMaterial = new THREE.LineBasicMaterial( { color: 0xAA00ff } );
    const lineChang = new THREE.LineSegments(changLineEdgesGeometry, changLineMaterial)
    cube.add(lineChang);
    //位置
    cube.position.set(10,10,10);
    //方向
    cube.rotation.x= Math.PI/8;
    cube.rotation.y= Math.PI/8;
    cube.rotation.z= Math.PI/8;
    scene.add(cube);



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