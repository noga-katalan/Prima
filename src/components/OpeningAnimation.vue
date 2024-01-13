<template>
    <div id="opening-animation">
        <img v-if="page !== 3" id="will" src="../assets/images/will.png" alt="person"/>
        <img v-if="page !== 3" id="hand" src="../assets/images/hand.png" alt="hand"/>
        <img id="chair" src="../assets/images/chair.png" alt="chair"/>
        <img id="typing-screen" src="../assets/images/typingScreen.png" alt="typingScreen"/>
        <button v-if="page === 0" @click="startAnimation" class="custom-btn btn-1 start-btn">התחל</button>
        <p v-if="page >= 1" id="typing-text">מלורם איפסום דולור סיט אמט, קונסקטורר אדיפיסינג אלית לורם איפסום דולור סיט אמט, קונסקטורר אדיפיסינג אלית..</p>
        <img v-if="page === 2" id="speech-bubble1" src="../assets/images/speechBubble1.png" alt="speech-bubble"/>
        <button @click="catRemoveFiles" v-if="page === 2" class="custom-btn btn-1 be-back-btn">נו טוב, כבר חוזר...</button>
        <img v-if="page === 3" id="cat" src="../assets/images/cat.png" alt="cat"/>
        <p v-if="page === 3" id="title">ובזמן שוויל הלך...</p>
        <img v-if="page === 4 || page === 5" id="speech-bubble2" src="../assets/images/speechBubble2.png" alt="speech-bubble"/>
        <p v-if="page === 5" id="text">פה אנחנו נכנסים לתמונה! ביחד, נצא למסע לשחזור הקבצים האבודים! מוכנים?</p>
        <button @click="nextScreen" v-if="page === 5" class="custom-btn btn-1 go-btn">בואו נלך על זה!</button>        
    </div>
</template>

<script>
export default {
  name: "opening-animation",
  props: [""],
  data() {
    return {
        page: 0
    }
  },
 methods: {
      startAnimation() {
        this.page++;
        setTimeout(() => {
            this.page = 2;
        }, 5000);
      },

      catRemoveFiles() {
        this.page++;
        this.$nextTick(() => {
            setTimeout(() => {
            document.getElementById("typing-text").style.display = "none";
            setTimeout(this.childReturns, 3500);
            }, 3000);
        });      
      },

      childReturns() {
        this.page++;
        setTimeout(() => {
            this.page++;
        }, 4000);
      },

      nextScreen() {
        this.$emit("next-screen", 1);
      }
    }
};
</script>

<style scoped>
* {
	margin: 0vh;
}

#opening-animation {
    width: 100vw;
    height: 100vh;
    background-image: url("../assets/images/roomFixed.svg");
    background-size: 100vw 100vh;
    background-repeat: no-repeat;
    overflow: hidden;
}

#chair {
    width: 31vw;
    height: 21vh;
    position: absolute;
    bottom: 0vh;
    right: 22vw;
    z-index: 2;
}

#will {
    width: 30vw;
    height: 55vh;
    position: absolute;
    bottom: 10vh;
    right: 22vw;
    z-index: 1;
}

#hand {
    width: 10vw;
    height: 30vh;
    position: absolute;
    bottom: 10vh;
    right: 47vw;
}

#typing-screen {
    width: 17vw;
    position: absolute;
    left: 22vw;
    top: 35vh;
    transform: rotate(-1deg);
}

#typing-text {
    color: black;
    width: 12vw;
    text-align: center;
    position: absolute;
    top: 40vh;
    left: 24.5vw;
    transform: rotate(-3deg);
}

#speech-bubble1 {
    width: 30vw;
    position: absolute;
    top: 10vh;
    right: 6vw;
}

#cat {
   position: absolute;
    top: 44vh;
    left: 28vw;
    animation: catAnimation 5s ease-in-out forwards;
}

#title {
    font-weight: bolder;
    color: white;
    direction: rtl;
    font-size: 3vw;
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    top: 6vh;
}

#speech-bubble2 {
    width: 28vw;
    height: 22vh;
    position: absolute;
    top: 12vh;
    left: 28vw;
}

#text {
    color: white;
    font-weight: bolder;
    direction: rtl;
    font-size: 2vw;
    text-align: center;
    width: 24vw;
    position: absolute;
    top: 10vh;
    right: 11vw;
}

/* buttons css */
button {
  margin: 20px;
}
.custom-btn {
  color: #fff;
  width: 130px;
  height: 40px;
  padding: 10px 25px;
  font-family: 'Lato', sans-serif;
  font-weight: 500;
  background: transparent;
  cursor: pointer;
  transition: all 0.3s ease;
  position: relative;
  display: inline-block;
}

.start-btn {
  position: relative;
  top: 11vh;
  left: 2vw;
  font-size: 2vh;
}

.be-back-btn {
    font-size: 1.5vh;
    width: 150px;
    height: 45px;
    position: relative;
    left: 35vh;
    top: 18vw;
}

.go-btn {
    font-size: 1.5vh;
    width: 160px;
    height: 45px;
    position: relative;
    left: 27vw;
    top: 22vh;
}

.btn-1 {
  border: none;
  border-radius: 10px;
  background-color: #ff9aff;
  box-shadow: 0 0 5px #ef97e8;
}

.btn-1:hover {
   box-shadow: 0 0 10px #ef97e8, 0 0 20px #ef97e8, 0 0 20px #fff inset;
}

@keyframes catAnimation {
    0% {
        transform: translateX(-1000px);
    }
    30% {
        transform: translateX(0px);
    }
    70% {
        transform: translateX(0px);
    }
    100% {
        transform: translateX(1000px);
    }
}

@keyframes textFade {
    0% {
        opacity: 1;
    }
    100% {
        opacity: 0;
    }
}
</style>