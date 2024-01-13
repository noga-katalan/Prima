<template>
  <div id="explanation-screen">
    <nav-bar :page="selectedItem" @update:page="switchPageNav"></nav-bar>
    <arrows @change-page="switchPageNav" :page="page"></arrows>
    <div class="explanation-content">
      <commands-snapshot v-if="page === 8" :page="page"></commands-snapshot>
      <snapshot-explanation v-if="page<9" :text="text" :page="page"></snapshot-explanation>
      <commands-ta v-if="page === 13" :page="page"></commands-ta>
      <ta-explanation v-if="page>=9 && page<14" :text="text" :page="page"></ta-explanation>
      <instructions v-if="page === 14" @start-game="startGame"></instructions>
    </div>
  </div>
</template>

<script>
import Arrows from '@/components/Arrows.vue'
import NavBar from '@/components/NavBar.vue'
import CommandsSnapshot from '@/components/CommandsSnapshot.vue'
import CommandsTa from '@/components/CommandsTa.vue'
import SnapshotExplanation from '@/components/SnapshotExplanation.vue'
import TaExplanation from '@/components/TaExplanation.vue'
import Instructions from '@/components/Instructions.vue'

import data from '../data.json'

export default {
  name: "explanation-screen",
  components: {
    Arrows,
    NavBar,
    CommandsSnapshot,
    CommandsTa,
    SnapshotExplanation,
    TaExplanation,
    Instructions
  },
  props: [""],
  data() {
    return {
      page: 0,
    };
  },
  computed: {
    text() {
      return data.explanation[this.page]; 
    },
    selectedItem() {
      return this.page.toString();
    },
  },
  methods: {
    switchPageNav(pageNum) {
      this.page = pageNum;
    },
    startGame() {
      this.$emit('start-game', 2);
    }
  }
};
</script>

<style scoped>
#explanation-screen {
    width: 100vw;
    height: 100vh;
    background-image: url("../assets/images/gradientBackground.png");
    background-size: 100vw 100vh;
    background-repeat: no-repeat;
    overflow: hidden;
}
</style>
