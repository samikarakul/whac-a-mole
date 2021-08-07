<template>
  <div id="game" >
      <router-link to="/">Change Difficulty Level or Username</router-link>

      <CurrentSetupInformation :username="username" :difficulty_level="difficulty_level"/>

      <PlayButton @startGame='startGame' :gameOver='isFinished'/>

      <div v-if="isPlaying">
        <GameInformations :lives="lives" :score="score" :username="username"/>
      </div>
      
      <div v-if="isFinished">
        <p>The Game Is Over. Your Score: {{ score }}</p>
        <ToggleScoreHistoryButton :showScoreHistory="showScoreHistory" @toggleShowScoreHistory="toggleShowScoreHistory"/>
      </div>

      <div v-if="showScoreHistory" class="userScoreHistory">
        <div v-for="user_score in scores" :key="user_score.user_id">
          <UserScore :user_score="user_score"/>
        </div>
      </div>
    
      <Target v-if="isPlaying" @targetFounded="raiseScore" @dicreaseLive="dicreaseLives" :difficulty_level="difficulty_level"/>
  </div>

</template>

<script>

import Target from '../components/Target.vue'
import UserScore from '../components/UserScore.vue'
import GameSetup from '../components/GameSetup.vue'
import PlayButton from '../components/PlayButton.vue'
import GameInformations from '../components/GameInformations.vue'
import ToggleScoreHistoryButton from '../components/ToggleScoreHistoryButton.vue'
import CurrentSetupInformation from '../components/CurrentSetupInformation.vue'
import hammer_small from '../assets/hammer_small.png'

export default {
  name: 'App',
  components: {Target, UserScore, GameSetup, PlayButton, GameInformations, ToggleScoreHistoryButton, CurrentSetupInformation},
  computed: {
      username(){
          if(localStorage.getItem('username') == '') localStorage.setItem('username', 'Anonym')
          return localStorage.getItem('username')
      },
      difficulty_level(){
          return localStorage.getItem('diff_lvl')
      }
  },
  created(){
      document.body.style.cursor = 'url("'+hammer_small+'"), default'
  },
  data(){
    return{
      isPlaying: false,
      isFinished: false,
      showScoreHistory: false,
      lives: 3,
      score: 0,
      select_err: '',
      scores: [],
      user_id: 0

    }
  },
  methods:{
    startGame(){
        this.lives = 3
        this.score = 0

        this.isPlaying = true
        this.isFinished = false
        this.showScoreHistory = false

    },
    raiseScore(targetScore)
    {
      this.score += 1
    },
    dicreaseLives()
    {
      if(this.lives > 1)
      {
        this.lives -= 1
      }
      else{
        this.isPlaying = false
        this.isFinished = true
        this.user_id += 1
        this.scores.push({
          'user_id': this.user_id,
          'username': this.username,
          'score': this.score,
          'difficulty_level': this.difficulty_level
        })
        
      }
    },
    toggleShowScoreHistory(){
      this.showScoreHistory = !this.showScoreHistory
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.userScoreHistory{
  height: 450px;
  width: 50%;
  padding-right: 50px;
  padding-left: 20px;
  margin-top: 20px;
  margin-right: auto;
  margin-left: auto;
  overflow-y: scroll;
  overflow-x: hidden;
  /* background: black; */
}

::-webkit-scrollbar {
  width: 15px;
}

/* Track */
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px grey; 
  border-radius: 10px;
}
 
/* Handle */
::-webkit-scrollbar-thumb {
  background: #5778C1;  
  border-radius: 10px;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #325FC3; 
}
</style>
