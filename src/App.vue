<template>
  <div :class="$style.container">

    <ScoreBoard :class="$style.score1" :score="score2" scoreName="score2" @increase="increase" @decrease="decrease"/>  


    <ScoreBoard :class="$style.score2" :score="score1" scoreName="score1" @increase="increase" @decrease="decrease"/>
    
    <div :class="$style.extras">
      <RandomSounds :class="$style.randomSounds"/>
      <GameWhistle :class="$style.gameWhistle" @game-whistle="whistle"/>
      <EraseScore :class="$style.eraseScore" @erase="eraseScore"/>      
    </div>
    
  </div>
</template>

<script>
import ScoreBoard from './components/ScoreBoard.vue';
import GameWhistle from './components/GameWhistle.vue';
import RandomSounds from './components/RandomSounds.vue'
import EraseScore from './components/EraseScore.vue'

import "@fontsource/montserrat"

export default {
  name: 'App',
  components: {
    ScoreBoard,
    RandomSounds,
    GameWhistle,
    EraseScore,
  },
  data(){
    return {
      score1: 0,
      score2: 0
    }
  },
  methods: {
    decrease(scoreName){
      if ( this[scoreName] > 0) {
        this[scoreName] --
      }
    },
    increase(scoreName){
        this[scoreName] ++
    },
    eraseScore(){
      this.score1 = 0
      this.score2 = 0
    },
    whistle() {
      const audio = new Audio('/instants/apito.mp3')
      audio.play()
    }
  }
}
</script>

<style lang="scss" module>
  .container {
    display: flex;
    flex: column;
    position: relative;

    height: 100vh;
    width: 100vw;

    @media (max-width: 880px) {
      flex-direction: column;

      height: 50vh;
      width: 100vw;
    }
  }

  .teamName1, .teamName2 {
    display: flex;
    position: fixed;
    width: 280px;
    flex: 1;
  }

  .teamName2 {
    left: 67.5%;
    top: 30vh;
    justify-content: center;
    align-self: center;

    @media (max-width:880px){
      left: 41.6%;
    }
  }

  .score1, .score2 {
    display: flex;
    flex: 1;

    justify-content: center;
    align-self: center;
    align-items: center;
    text-align: center;
    
    font-family: 'Montserrat';
    font-size: 150px;
    font-weight: bold;
    color: #fff;
    bottom: 0;
    padding: 16px;
    
    background-color: transparent;
    border: none;
    
    height: 100%;
    width: 100%;

    @media (max-width: 880px) {
      display: flex;
      flex-direction: column;

      bottom: 0; 
    }
  }

  .score1 {
    display: flex;
    flex-direction: column;

    background: var(--team1);
  }

  .score2 {
    display: flex;
    flex-direction: column;

    background: var(--team2);
  }

  .extras {
    display: flex;
    position: absolute;
    justify-content: center;
    align-self: center;
    gap: 24px;
    
    width: 100%;
    bottom: 12px;
    @media (max-width: 880px){
      flex-direction: column;

      height: 100vh;
      
      margin-top: 32px;
      bottom: unset;      
      left: 10px;
    }
  }

  .randomSounds, .gameWhistle, .eraseScore  {
    font-family: 'Montserrat';
    font-weight: 700;
    font-size: 10px;
    text-transform: uppercase;
    color: var(--team2);

    width: 64px;
    height: 64px;

    padding: 0;
    border: none;
    border-radius: 50%;

    @media (min-width: 880px){
      width: 83px;
      height: 83px;
      font-size: 18px;
      color: var(--team2);
  }
}

</style>

