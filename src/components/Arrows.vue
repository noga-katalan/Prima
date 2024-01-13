<template>
  <div id="arrows" :class="{ 'no-back-arrow': currentPage === 0 }">
    <div class="arrow-wrapper" v-if="currentPage !== 0">
      <div class="circle" @click="changePage('back')">
        <img src="../assets/images/circle.png" alt="circle" class="circle-img">
        <img src="../assets/images/backArrow.png" alt="backArrow" class="arrow back">
      </div>
    </div>
    <div class="arrow-wrapper forward-arrow" v-if="currentPage < 14">
      <div class="circle" id="forward" @click="changePage('forward')">
        <img src="../assets/images/circle.png" alt="circle" class="circle-img">
        <img src="../assets/images/continueArrow.png" alt="continueArrow" class="arrow forward">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "arrows",
  props: ["page"],
  computed: {
    currentPage: {
      get() {
        return this.page;
      },
      set(value) {
        this.$emit("change-page", value);
      }
    }
  },
  methods: {
    changePage(direction) {
      if (direction === "forward") {
        this.currentPage++;
      } else if (direction === "back" && this.currentPage !== 0) {
        this.currentPage--;
      }
    }
  }
};
</script>

<style scoped>
#arrows {
  position: absolute;
  top: 10vh;
  left: 0;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 100vh;
}

.circle {
  position: relative;
  display: inline-block;
}

.circle-img {
  width: 70px;
  height: 70px;
}

.arrow {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 50px;
  transition: transform 0.3s ease;
}

.forward {
  right: -1vw;
}

.arrow:hover {
  transform: translate(-50%, -50%) translateX(5px);
  cursor: pointer;
}
.no-back-arrow .forward-arrow {
  margin-right: 93vw;
}
</style>