<!-- <script setup>
import HelloWorld from './components/HelloWorld.vue'
import { ref } from 'vue'
const count1 = ref(0);
const count2 = ref(0);
function click1(){            // @click="count1++"
  count1.value += 1 ;
 }
function click2(){              //@click="count2+=10"
   count2.value += 10;  
 }
</script>

<template>
  <div>
 
      <img src="/vite.svg" class="logo" alt="Vite logo" @click=click1() /> {{ count1 }}   


      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" @click=click2() /> {{ count2 }}
 
  </div>
  <HelloWorld msg="Vite + Vue" />
</template>

<style scoped>

.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style> -->

<script setup>
import { ref } from 'vue'

const random = ['ค้อน', 'กระดาษ', 'กรรไกร', 'ความรัก'];
const botRandom = ref('');
const playerRandom = ref('');
const botScore = ref(0);
const playerScore = ref(0);
const tieScore = ref(0);

//  src  pic = https://pixabay.com
//           = https://images.unsplash.com

function RandomImg(pic) {
  const allImgs = {
    'ค้อน': 'https://cdn.pixabay.com/photo/2014/03/25/15/26/rock-paper-scissors-296854_1280.png',
    'กระดาษ': 'https://cdn.pixabay.com/photo/2014/03/25/15/26/rock-paper-scissors-296855_640.png',
    'กรรไกร': 'https://cdn.pixabay.com/photo/2014/03/25/15/26/rock-paper-scissors-296853_640.png',
    'ความรัก': 'https://images.unsplash.com/photo-1571172964276-91faaa704e1f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80',
  };

  return allImgs[pic];
}

function playButton() {
  botRandom.value = random[Math.floor(Math.random() * random.length)];
  playerRandom.value = random[Math.floor(Math.random() * random.length)];

  if (
    (botRandom.value === 'ค้อน' && playerRandom.value === 'กรรไกร') ||
    (botRandom.value === 'กระดาษ' && playerRandom.value === 'ค้อน') ||
    (botRandom.value === 'กรรไกร' && playerRandom.value === 'กระดาษ') ||
    (botRandom.value === 'ความรัก' && playerRandom.value === 'กรรไกร') ||
    (botRandom.value === 'ความรัก' && playerRandom.value === 'ค้อน') ||
    (botRandom.value === 'ความรัก' && playerRandom.value === 'กระดาษ')
  ) {
    botScore.value++;
  } else if (
    botRandom.value === playerRandom.value
  ) {
    tieScore.value++;
  } else {
    playerScore.value++;
  }
}

function resetGame() {
  botRandom.value = '';
  playerRandom.value = '';
  botScore.value = 0;
  playerScore.value = 0;
}
</script>

<template>
  <div class="container">
    <div class="box-1">
      <h2 style="color: red;">Bot - ボット</h2>

      <img class="size-img" :src="RandomImg(botRandom)" /><br>
      {{ botRandom }}
    </div>
    <div class="vs-text">
      <p>vs</p>
    </div>
    <div class="box-2">
      <h2 style="color: rgb(69, 202, 255);">Player - プレーヤー</h2>

      <img class="size-img" :src="RandomImg(playerRandom)"  /><br>
      {{ playerRandom }}
    </div>
  </div>
  <div class="text-score">
    <p style="color: red;">Point of Bot : &nbsp; {{ botScore }}</p>
    <p style="color: burlywood;">Tie : {{ tieScore }}</p>
    <p style="color: rgb(69, 202, 255);"> Point of Player : &nbsp; {{ playerScore }}</p>
  </div>
  <button class="bt-play" @click="playButton" style="background-color: rgb(119, 198, 0);">Play</button> &nbsp;
  <button class="bt-reset" @click="resetGame" style="background-color: red;">Resetto</button>
</template>

<style>
.vs-text {
  color: blue, red;
  font-weight: bold;;
  font-size: 35px;
  font-weight: bold;
  text-align: center;
  margin-top: 100px;
  margin-left: 25px;
  margin-right: -5px;
}

.text-score {
  justify-content: space-between;
  margin: 5px 20px;
}

.container {
  display: flex;
}

.box-1, .box-2 {
  margin: 10px 20px;
}

.bt-play {
  margin: 10px 20px;
  transition: 300ms;
}

.bt-play:hover {
  transform: scale(1.09);
  box-shadow: 0 8px 10px 0 rgb(0, 255, 132);
}

.bt-reset {
  transition: 300ms;
}

.bt-reset:hover {
  box-shadow: 0 8px 10px 0 rgb(255, 89, 0);
  transform: scale(1.09);
}

.size-img {
  border-radius: 50%;
  border: none;
  width: 150px;
  height: 150px;
}
</style>

