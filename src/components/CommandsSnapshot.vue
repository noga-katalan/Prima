<template>
  <div id="commands">
      <div class="command-container">
        <pre v-pre class="command" >
          L-n &lt;<span>L&gt;</span> -L <span>&lt;L&gt;</span> -s <span>&lt;V&gt;&lt;L&gt;</span>
        </pre>
        <div class="span0" :class="spanClass" @mouseenter="saveSpanNum" @mouseleave="hoveredSpan = -1"></div>
        <div class="span1" :class="spanClass" @mouseenter="saveSpanNum" @mouseleave="hoveredSpan = -1"></div>
        <div class="span2" :class="spanClass" @mouseenter="saveSpanNum" @mouseleave="hoveredSpan = -1"></div>

        <p v-if="hoveredSpan != '-1'" class="explanations">{{explanationsArray[hoveredSpan]}}</p>
      </div>

      <div class="command-container">
        <pre v-pre class="command">
           <span>&lt;L&gt;</span> <span>&lt;D&gt;</span>
        </pre>
        <div class="span3" :class="spanClass" @mouseenter="saveSpanNum" @mouseleave="hoveredSpan = -1"></div>
        <div class="span4" :class="spanClass" @mouseenter="saveSpanNum" @mouseleave="hoveredSpan = -1"></div>
      </div>

      <p id="guide-text">עברו עם העכבר מעל חלקי הקוד המסומנים על מנת לחשוף את ההסבר!</p>
  </div>
</template>

<script>
export default {
  name: "commands",
  props: ["page"],
  data() {
    return {
      explanationsArray: ["לורם איפסום", "לורם איפסום", "לורם איפסום","לרום איפסום", "לרום איפסום"],
      hoveredSpan: -1,
      spanClass: `span${this.hoveredSpan}`
    };
  },
  methods: {
      saveSpanNum(event) {
        const hoveredElement = event.currentTarget;
        const hoveredSpanClass = hoveredElement.classList[0];

        this.hoveredSpan = hoveredSpanClass.slice(4);
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

.span4 {
  width: 8vw;
  height: 3vh;
  position: absolute;
  top: 17.3vh;
  left: 26vw;
}

.span3 {
  width: 5vw;
  height: 3vh;
  position: absolute;
  top: 17.3vh;
  left: 21vw;
}

.span2 {
  width: 9vw;
  height: 3vh;
  position: absolute;
  top: 17.3vh;
  left: 27vw;
}

.span1 {
  width: 4vw;
  height: 3vh;
  position: absolute;
  top: 17.3vh;
  left: 22vw;  
}

.span0 {
  width: 5vw;
  height: 3vh;
  position: absolute;
  top: 17.3vh;
  left: 15vw;
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
  right: 22vw;
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