<template>
  <div id="game-screen" :style="backgroundStyle">
    <transition name="fade">
      <div v-if="showFiles" class="files-container">
        <img v-for="index in 7" :key="index" src="../assets/images/yellowFile.png" alt="file">
      </div>
    </transition>
      <img v-if="showQuestion===true" src="../assets/images/typingScreen.png" alt="typing-screen">
  </div>
</template>

<script>
export default {
  name: "game-screen",
  data() {
    return {
      animation: "zoom-in 5s forwards alternate",
      showFiles: false,
      backgroundStyle: {
        backgroundImage: require("../assets/images/fullBackground.svg"),
        backgroundSize: "100%",
        backgroundPosition: "50% 0",
        showQuestion: 0
      }
    };
  },
  mounted() {
    setTimeout(() => {
      this.showFiles = true;
      this.animateBackground();
    }, 5500);
  },
  methods: {
    animateBackground() {
      setTimeout(() => {
        this.backgroundStyle = {
          backgroundImage: require("../assets/images/computer.png"),
          backgroundSize: "cover",
          backgroundPosition: "center",
          transition: "background-image 0s"
        };
      }, 5000);
    }
  }
};
</script>

<style scoped>
* {
  margin: 0;
}

#game-screen {
  width: 100vw;
  height: 100vh;
  background-image: url("../assets/images/fullBackground.svg");
  background-repeat: no-repeat;
  overflow: hidden;
  animation: zoom-in 5s forwards alternate;
  background-position: 50% 0;
  position: relative;
}

@keyframes zoom-in {
  0% {
    background-size: 100%;
  }
  100% {
    background-size: 280%;
    background-position: calc(45% + 50vw) -80vh; 
  }
}

.files-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: right;
  position: absolute;
  top: 35vh;
  left: 70vw;
  transform: translate(-50%, -50%);
  width: 30vw;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

img {
  width: 5vw;
  margin: 1vh;
}

/* Adjust the width and margin to fit your layout */
@media (max-width: 768px) {
  img {
    width: 8vw;
    margin: 1.5vh;
  }
}

#typing-screen {
  width: 10vw;
  height: 10vh;
}
</style>
