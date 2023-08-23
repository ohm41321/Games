<script setup>
import { ref } from 'vue'
import { reactive } from 'vue';
defineProps({
  msg: String,
})

const count = ref(0);
let name = ref('Fontez');

const x = ref(0);
const y = ref(0);
const ans = ref(0);
function cal(){
  ans.value = x.value + y.value
}


const styleObject = reactive({
  color: 'orange',
  fontSize: '13px'
});

function bttext() {
  count.value += 1;
  styleObject.fontSize = parseInt(styleObject.fontSize) + 5 + 'px';
}
let lightStatus = ref(false);

function light(){
  lightStatus.value = !lightStatus.value;
  if (lightStatus == false) {
      lightStatus == "The Light is Off";
  }
  else if(lightStatus == true){
      lightStatus == "The Light is On";
  }
}

</script>

<template>
  <h1>{{ msg }}</h1>
  <h2 :style="styleObject">{{ name }}</h2>

  <form>
   Name &nbsp; <input type="text" id="fname" name="fname" v-model="name" >
   <br>
   บวกเลข
   <input type="number" v-modal="x"> + 
   <input type="number" v-modal="y">  
<br>
   <button @click="cal()">คำตอบ</button> &nbsp; {{ ans }}

  </form>




  <div class="card">
    <button @click="light()">Turn On/Off the Light </button> <a>&nbsp; {{ lightStatus }} &nbsp;</a>
    <button type="button" @click=bttext()>count is {{ count }}</button>
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
.lighton{
  background-color: rgba(0,0,0, 0.5) ;
}
</style>
