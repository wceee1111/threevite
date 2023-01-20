<script setup lang="ts">
import { ref,reactive,toRefs,getCurrentInstance } from 'vue'
import * as THREE from 'three'
const scene = new THREE.Scene()//场景
const carmera = new THREE.PerspectiveCamera(
    75,
    window.innerWidth / window.innerHeight,
    0.1,
    1000
)//相机


//添加相机
carmera.position.set(0, 0, 10)
scene.add(carmera)

defineProps<{ msg: string }>()
let test = ref<string>('bestvite')
const count = ref(0)

const d = reactive([1,2,3,4])
let b=[1,2,3,4,5]
d.push(...b);

const instance = getCurrentInstance()

instance?.proxy?.$Bus.on('chuanchanceshi',(str)=>{
    console.log(str,"==========>B");
    

})



</script>

<template>
  <!-- <h1>{{ name }},{{boon}}</h1> -->
  <h2>这里是B</h2>

  <div class="card">
    <!-- <button type="button" @click="testc">测试</button> -->
    <button type="button" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
