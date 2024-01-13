<template>
  <div id="commands-ta">
    <div class="command-container">
      <pre v-pre class="command">
        t-c &lt;<span>P</span>&gt;/&lt;<span>f</span>.t &lt;<span>D</span>&gt;
      </pre>
      <div v-for="i in 3" :key="i" :class="`span${i - 1}`" @mouseenter="saveSpanNum(i - 1)" @mouseleave="hoveredSpan = -1"></div>
      <p v-if="hoveredSpan !== -1" class="explanations">{{ explanationsArray[hoveredSpan] }}</p>
    </div>
    <p id="guide-text">עברו עם העכבר מעל חלקי הקוד המסומנים על מנת לחשוף את ההסבר!</p>
  </div>
</template>

<script>
export default {
  name: "commands-ta",
  props: ["page"],
  data() {
    return {
      explanationsArray: [
        "",
        "לורם איפסום",
        "לרום איפסום"
      ],
      hoveredSpan: -1
    };
  },
  methods: {
    saveSpanNum(spanNum) {
      this.hoveredSpan = spanNum;
    }
  }
};
</script>

<style>
#guide-text {
  font-size: 3vh;
  color: white;
  position: absolute;
  bottom: 15vh;
  left: 24vw;
}

.span2 {
    width: 6.5vw;
    height: 3vh;
    position: absolute;
    top: 17.3vh;
    left: 25.5vw;
}

.span1 {
    width: 3.5vw;
    height: 3vh;
    position: absolute;
    top: 17.3vh;
    left: 19vw;
}

.span0 {
    width: 3vw;
    height: 3vh;
    position: absolute;
    top: 17.3vh;
    left: 15.5vw;
}

.explanations {
  color: white;
  font-size: 3vh;
  position: absolute;
  border-style: solid;
  color: white;
  background-color: black;
  border-color: black;
  border-width: 1px;
  border-radius: 25px;;
  padding: 10px 70px;
  top: 47vh;
  right: 1vw;
  width: 40vw;
}

span {
  background-color: rgba(0, 0, 255, 0.329);
}

.command {
  position: absolute;
  left: 46%;
  top: 50%;
  transform: translate(-50%, -50%);
  font-size: 1.5vh;
  color: white;
  width: 39vw;
  background-color: transparent;
  direction: ltr;
}

.command-container {
  width: 43vw;
  height: 40vh;
  background-image: url("");
  background-size: 100% 100%;
  position: relative;
  display: inline-block;
  left: 1vw;
  top: 39vh;
}
</style>