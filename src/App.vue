<script setup>
import { ref } from 'vue'
import GameAlternatives from './components/GameAlternatives.vue';
import GameScore from './components/GameScore.vue'
import GameResult from './components/GameResult.vue'

const alternative = ref("")
const compAlternative = ref("")
const winnerInfo = ref("")
const winner = ref('')
const round = ref(0) // Vi behöver räkna omgångarna

function setWinnerInfo (_winner) {
  winner.value = _winner
  round.value++ // Öka räknaren för varje omgång
  if(_winner === "draw") {
    winnerInfo.value = "It's a draw!"
  } else if ((_winner === 'user')) {
    winnerInfo.value = "Du vann, du fuskade säkert :("
  } else { 
    winnerInfo.value = "Än en gång besegrade maskinen människan!"
  }
}

//Sätt båda alternativen till "alt" parametrar

function setUserAlternative (alt) {
  alternative.value = alt
}

function setComputerAlternative (alt) {
  compAlternative.value = alt
}
</script>

<template>
  <h1>Sten Sax Påse!</h1>
  <!--Val, ställning, result och button -->
  <GameAlternatives 
  @user-choice="setUserAlternative" 
  @computer-choice="setComputerAlternative" 
  @winner="setWinnerInfo"
  />
  <GameScore 
  :user-alternative="alternative" 
  :computer-alternative="compAlternative" 
  :winner-info="winnerInfo"
  />
  <GameResult :result="{round, winner}"/>
  <button onclick="location.reload()" id="LaddaOm">Nytt försök!</button>
</template>

<style scoped>

h1 {
  margin:auto;
}
#LaddaOm {
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  cursor: pointer;
  border-radius: 10px;
}

</style>
