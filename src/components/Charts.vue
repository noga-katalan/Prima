<template>
  <div id="charts">
    <p id="info" class="expScreen info">{{ info }}</p>
    <p class="expScreen text">{{ text }}</p>
    <div class="background-container">
      <img class="chart" :src="chartSrc" alt="chart">
      <div class="btns-container">
        <button v-for="btn in buttons" :key="btn.value" class="daysBtns" @click="changeDay(btn.value)">
          {{ btn.label }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import data from '../data.json'

export default {
  name: "charts",
  props: ["page"],
  computed: {
    buttons() {
      return this.page === 7 ? [
        { label: "Day 1", value: '1' },
        { label: "Day 2", value: '2' }
      ] : [
        { label: "Day 1", value: '1' },
        { label: "Day 2", value: '2' },
        { label: "Day 3", value: '3' }
      ];
    },
    text() {
      if (this.page === 7) {
        return data.chart2[this.day];
      } else {
        return data.chart1[this.day];
      }
    },
    info() {
      if (this.page === 7) {
        return data.chart2[0];
      } else {
        return data.chart1[0];
      }
    },
  },
  data() {
    return {
      chartSrc: this.initialChartSrc(),
      day: 1,
    };
  },
  methods: {
    changeDay(dayNum) {
      // this.chartSrc = require(`/chart${this.page === 7 ? '2' : '1'}_${dayNum}.png`);
      this.day = dayNum;
    },
    initialChartSrc() {
      // return require(`s/chart${this.page === 7 ? '2' : '1'}_1.png`);
    }
  }
};
</script>

<style scoped>
.chart {
  position: absolute;
  width: 50vw;
  height: 59vh;
  top: 4vh;
  right: 2vw;
}

.background-container {
  background-image: url('/img/gradientBackground.767ea25a.png');
  background-size: 100% 100%;
  width: 55vw;
  height: 77vh;
  position: absolute;
  top: 16vh;
  right: 35vw;
  display: inline-block;
  border-radius: 60px;
  border-style: outset;
}

.btns-container {
  position: absolute;
  top: 70vh;
  right: 7vw;
  width: 40vw;
  display: flex;
  justify-items: stretch;
  justify-content: space-around;
}

.daysBtns {
  background-color: rgb(187, 187, 187);
  width: 12vw;
  height: 5vh;
  border-radius: 11px;
  font-weight: 600;
  border-style: none;
}

button:focus { 
  background-color: gray; 
} 

.expScreen {
  color: white;
  width: 25vw;
  position: absolute;
  top: 10vh;
  right: 7vw;
  font-size: 2vh;
  text-align: right;
}

.info {
  top: 40vh;
}

.text {
  top: 48vh;
}
</style>