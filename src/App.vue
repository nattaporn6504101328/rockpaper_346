<template>
  <div id="app">
    <h1>✌️✊🖐️เกมเป่ายิ้งฉุบ🖐️✊✌️</h1>
    <RockPaperScissorsComponent/>
  </div>
</template>

<script>
import RockPaperScissors from './components/RockPaperScissors.vue';
import RockPaperScissorsComponent from './components/RockPaperScissors.vue';
export default {
  components: {
    RockPaperScissorsComponent,
    RockPaperScissors
},
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Itim&display=swap');
#app {
  font-family: 'Itim', cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #5f5c5c;
  background-color:  #DBE8E7;
  width: 97%; /* ให้ความกว้างเต็มหน้าจอ */
  height: 100vh; /* ให้ความสูงเต็มหน้าจอ */
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 20px;
}
h1 {
  margin-top: 0px;
  text-shadow: 4px 4px 8px rgb(255, 255, 255);
  font-weight: bold;
  margin-bottom: 0px;
  font-size: 2.5em;
  /*margin-bottom: 0px; /* ปรับระยะห่างด้านล่างของ <h1> */
}
h2{
  font-size: 1.5em;
  margin-bottom: 10px;
}
.container {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-top: 20px;
}
.player {
  flex: 1;
  text-align: center;
  margin: 0 5px;
  padding: 30px; /* ปรับระยะห่างรอบขอบของผู้เล่น */
}
.player-info {
  font-size: 20px; /* เพิ่มขนาดตัวอักษรเป็น 20px (ปรับแต่งตามที่คุณต้องการ) */
}
.bottom-section {
  margin-top:10px; /* ปรับระยะห่างด้านบนของส่วนคะแนนรวม */
  text-align: center;
}
.bottom-section,
.player {
  margin-top: 10px; /* ปรับระยะห่างด้านบนระหว่างคะแนนและ player */
}
.bottom-section button {
  margin: 10px; /* ปรับระยะห่างรอบขอบของปุ่ม */
  background-color:  #00455F;
  color: white;
}
.bottom-section button:hover{
  background-color: #e74d3c61;
}
.end-game-button {
  background-color: #e74d3cc2;
  color:#ffffff;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}
.end-game-button:hover {
  background-color: #ee3c3c81;
}
img{
  width: 80px; 
  height: 80px;
}
</style>