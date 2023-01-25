<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from './components/HelloWorld.vue'
import B from './components/B.vue'
import * as THREE from 'three'
import { onMounted } from 'vue';
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js'
const scene = new THREE.Scene()//场景
const camera = new THREE.PerspectiveCamera(
    75,
    window.innerWidth / window.innerHeight,
    0.1,
    1000
)//相机

//tGGDD
//添加相机

camera.position.set(0, 0, 10)
scene.add(camera)
//添加集合体
const cubeGeometry = new THREE.BoxGeometry(1,1,1)
const cubeMaterial = new THREE.MeshBasicMaterial({color:0x00ff00,transparent:0,opacity:0.5})
const cube =new THREE.Mesh(cubeGeometry,cubeMaterial)
const axesHelper = new THREE.AxesHelper(5);
scene.add(axesHelper)//辅助线
scene.add(cube)//渲染

//初始化渲染器
const renderer = new THREE.WebGLRenderer()
renderer.setSize(window.innerWidth,window.innerHeight)
console.log(renderer );
onMounted(()=>{
  // document.getElementById('mythree')?.appendChild(renderer.domElement)
  document.body.appendChild(renderer.domElement)
})
renderer.render(scene,camera);
//创建轨道控制器
const controls = new OrbitControls(camera,renderer.domElement);
const render = ()=>{
  renderer.render(scene,camera);
  requestAnimationFrame(render);
}

render();
</script>

<template>
  <div id="mythree"></div>
  <!-- <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <HelloWorld msg="Vite + Vue" />
  <B msg="bbb" /> -->
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
