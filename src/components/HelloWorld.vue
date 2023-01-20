<script setup lang="ts">
import { ref,reactive,toRefs,getCurrentInstance } from 'vue'

defineProps<{ msg: string }>()
let test = ref<string>('bestvite')
const count = ref(0)

const d = reactive([1,2,3,4])
let b=[1,2,3,4,5]
d.push(...b);


const instance = getCurrentInstance()

const emit = () => {
  instance?.proxy?.$Bus.emit('chuanchanceshi','mitt')
}




</script>

<template>
  <!-- <h1>{{ name }},{{boon}}</h1> -->
  <h2>obj{{ d }}</h2>

  <div class="card">
    <!-- <button type="button" @click="testc">测试</button> -->
    <button type="button" @click="count++">count is {{ count }}</button>
    <button @click="emit">emit</button>
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
