<template>
  <div id="ta-explanation">
        <h1 v-if="page!==9">לורם איפסום</h1>
        <img v-if="page!==9" id="line" src="../assets/images/line.png" alt="line">
         <h2 v-if="page>9 && page<=11">אז מהו בעצם  ?</h2>
         <h2 v-if="page>11 && page<=12">למה אנחנו צריכים את זה?</h2>
         <h2 v-if="page>12">איך ניצור אותם?</h2>
        <p id="expScreen" :class="{ 'up-text': page === 10 }">{{ text }}</p>
        <ta-example v-if="page===10"></ta-example>
        <file-drag v-if="page===9"></file-drag>
  </div>
</template>

<script>
import TaExample from '@/components/TaExample.vue'
import FileDrag from '@/components/FileDrag.vue'

export default {
  name: "ta-explanation",
   components: {
    TaExample,
    FileDrag
  },
  props: ["text", "page"],
  data() {
    return {
    };
  },
  methods: {
    }
};
</script>

<style scoped>
#ta-explanation {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  text-align: center;
}

#expScreen {
    width: 60vw;
    font-size: 3vh;
    color: white;
    margin-top: 10vh;
    z-index: 3;
}

h1 {
  font-size: 6vh;
  color: white;
  font-weight: 700;
  position: absolute;
  top: 23vh;
}

h2 {
    font-size: 3vh;
    color: white;
    font-weight: 600;
    position: absolute;
    top: 33vh;
}

#line {
    position: absolute;
    top: 32vh;
    width: 30vw;
}

.up-text {
  position: absolute;
  top: 30vh;
}

</style>

