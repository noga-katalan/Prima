<template>
  <div id="app">    
    <opening-animation v-if="screen===0" @next-screen="switchScreen"></opening-animation>
    <explanation-screen v-if="screen===1" @start-game="switchScreen"></explanation-screen>
    <game-screen v-if="screen===2"></game-screen>
    <ending-screen v-if="screen===3"></ending-screen>
  </div>
</template>

<script>
import OpeningAnimation from '@/components/OpeningAnimation.vue'
import GameScreen from '@/components/GameScreen.vue'
import EndingScreen from '@/components/EndingScreen.vue'
import ExplanationScreen from '@/components/ExplanationScreen.vue'

export default {
  name: 'app',
  components: {
    OpeningAnimation,
    GameScreen,
    EndingScreen,
    ExplanationScreen
  },
  data() {
    return {
      screen: 0,
      }
    },
  methods: {
    switchScreen(Screen) {
      this.screen = Screen;
    },
    startOver() {
      this.screen = 0;
    }
  },
};
</script>

<style>
@font-face {
  font-family: "Assistant-light";
  src: url("./assets/fonts/Assistant-Light.ttf");
}

* {
  direction: rtl;
  text-align: center;
  font-family: "Assistant-light";
}

#app {
  width: 100%;
  height: 100%;
}

</style>