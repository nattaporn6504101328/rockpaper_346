<script>
export default {
  data() {
    return {
      player1Score: 0,
      player2Score: 0,
      gameResult1: null,
      gameResult2: null,
      player1Choice: null, // เพิ่มตัวแปรเพื่อเก็บคำว่าค้อน กระดาษ หรือ กรรไกร
      player2Choice: null, // เพิ่มตัวแปรเพื่อเก็บคำว่าค้อน กระดาษ หรือ กรรไกร
      choices: ['ค้อน', 'กระดาษ', 'กรรไกร','ความรัก'],
      gameStarted: false,
      winner: null, // เพิ่มตัวแปรเพื่อเก็บข้อมูลผู้ชนะหรือเสมอ
    };
  },
  methods: {
    startGame() {
      this.gameStarted = true; // เริ่มเกม
      this.winner = null; // ล้างผลสรุปเมื่อเริ่มเกมใหม่
    },
    playRound() {
      // สุ่มเลือกคำว่า ค้อน, กระดาษ หรือ กรรไกร สำหรับผู้เล่นทั้งสองฝ่าย
      const player1Index = Math.floor(Math.random() * this.choices.length);
      const player2Index = Math.floor(Math.random() * this.choices.length);
      const player1Choice = this.choices[player1Index];
      const player2Choice = this.choices[player2Index];
      // กำหนดผลลัพธ์ของเกมสำหรับแต่ละฝ่าย
      if (player1Choice === player2Choice) {
        this.gameResult1 = 'เสมอ';
        this.gameResult2 = 'เสมอ';
      } else if (
        (player1Choice === 'ค้อน' && player2Choice === 'กรรไกร') ||
        (player1Choice === 'กระดาษ' && player2Choice === 'ค้อน') ||
        (player1Choice === 'กรรไกร' && player2Choice === 'กระดาษ') ||
        (player1Choice === 'ความรัก' && player2Choice !== 'ความรัก') 
      ) {
        this.gameResult1 = 'ชนะ';
        this.gameResult2 = 'แพ้';
        this.player1Score++;
      } else if (
        (player2Choice === 'ความรัก' && player1Choice !== 'ความรัก')
      ) {
        this.gameResult1 = 'แพ้';
        this.gameResult2 = 'ชนะ';
        this.player2Score++;
      }
      else {
        this.gameResult1 = 'แพ้';
        this.gameResult2 = 'ชนะ';
        this.player2Score++;
      }
      // บันทึกคำว่าผู้เล่นได้เลือกค้อน กระดาษ หรือ กรรไกร
      this.player1Choice = player1Choice;
      this.player2Choice = player2Choice;
       this.winner = null; // ล้างผลสรุปก่อนเริ่มเกมใหม่
    },
    resetGame() {
      // สรุปผู้ชนะหรือการเสมอกัน
  if (this.player1Score > this.player2Score) {
    this.winner = 'ผู้เล่น 1 ชนะ!';
  } else if (this.player2Score > this.player1Score) {
    this.winner = 'ผู้เล่น 2 ชนะ!';
  } else {
    this.winner = 'เกมเสมอ';
  }
      this.player1Score = 0;
      this.player2Score = 0;
      this.gameResult1 = null;
      this.gameResult2 = null;
      this.player1Choice = null;
      this.player2Choice = null;
      this.gameStarted = false; // รีเซ็ตเกมให้เริ่มใหม่
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="player">
      <h2>ผู้เล่น 1</h2>
      <div>
        <img v-if="!gameStarted && player1Choice === null" src="./assets/start.png" alt="เริ่มเกม" @click="startGame" />
        <img v-if="player1Choice === 'ค้อน'" src="./assets/rock2.png" alt="ค้อน" />
        <img v-if="player1Choice === 'กระดาษ'" src="./assets/paper2.png" alt="กระดาษ" />
        <img v-if="player1Choice === 'กรรไกร'" src="./assets/Scissors2.png" alt="กรรไกร" />
        <img v-if="player1Choice === 'ความรัก'" src="./assets/h2.png" alt="ความรัก" />
      </div>
      <div class="player-info">
      <div>ผล: {{ gameResult1 }}</div>
      <div>คะแนน: {{ player1Score }}</div>
    </div>
  </div>
    <div class="player">
      <h2>ผู้เล่น 2</h2>
      <div>
        <img v-if="!gameStarted && player2Choice === null" src="./assets/start.png" alt="เริ่มเกม" @click="startGame" />
        <img v-if="player2Choice === 'ค้อน'" src="./assets/rock1.png" alt="ค้อน" />
        <img v-if="player2Choice === 'กระดาษ'" src="./assets/paper1.png" alt="กระดาษ" />
        <img v-if="player2Choice === 'กรรไกร'" src="./assets/Scissors1.png" alt="กรรไกร" />
        <img v-if="player2Choice === 'ความรัก'" src="./assets/h2.png" alt="ความรัก" />
      </div>
      <div class="player-info">
      <div>ผล: {{ gameResult2 }}</div>
      <div>คะแนน: {{ player2Score }}</div>
    </div>
  </div>
  </div>

    <div class="bottom-section">
      <div>
      <h2>คะแนน</h2>
      <div><span class="player-info">{{ player1Score }} : {{ player2Score }}</span></div>
    </div>
    <div>
      <button @click="playRound">เป่ายิ้งฉุบ</button>
      <span style="margin-right: 20px;"></span>
      <button @click="resetGame">เริ่มใหม่</button>
    </div>
    <!-- เพิ่มส่วนนี้เพื่อแสดงผลผู้ชนะหรือการเสมอกัน -->
<div v-if="winner !== null">
  <h2>ผลสรุป</h2>
  <p>{{ winner }}</p>
</div>
  </div>
</template>



