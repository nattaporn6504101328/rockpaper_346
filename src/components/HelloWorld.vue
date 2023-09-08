<script setup>
import { ref } from 'vue';
import { reactive } from 'vue';

defineProps({
  msg: String,
});

const x = ref(0);
const y = ref(0);
const answer = x.value + y.value;

const count = ref(0);
let name = ref('Tanyaluk');
const lightStatus = ref(true);

function turnOn(){
  lightStatus.value = !lightStatus.value;
}

const styleObject = reactive({
  color: 'red',
  fontSize: '50px',
});

function upsize(){
  count.value++;

  //"50px" --> "50"
  console.log(styleObject.fontSize.slice(0,-2));

  //"50" --> 50
  let fsize = parseInt(styleObject.fontSize.slice(0,-2));

  styleObject.fontSize = fsize + count.value + "px";
}
</script>

<template>
  <h1>{{ msg }}</h1>
  <h2 :style="styleObject">{{ name }}</h2>


  <form>
    ชื่อ <input type="text" v-model="name">
    <br>
    บวกเลข
    <input type="number" v-model="x"> +
    <input type="number" v-model="y">
    <br>
    {{answer}}

  </form>




  <div class="card">
  <button @click="turnOn()">On/Off</button> {{ lightStatus }}
    <button type="button" @click="upsize()">count is {{ count }}</button>
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
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
