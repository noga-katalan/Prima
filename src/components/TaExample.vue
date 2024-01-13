<template>
  <div id="ta-example">
    <img class="box-animation" src="../assets/images/closedBox.png" alt="box">
    <img id="arrow" src="../assets/images/animationArrow.png" alt="arrow">
    <div class="people-conatainer">
        <img src="../assets/images/person.png" alt="person1">
        <img src="../assets/images/person.png" alt="person2">
    </div>
    
  </div>
</template>
 
<script>
export default {
    name: "ta-example",
    props: [""],
  data() {
    return {

    };
  },
  methods: {
    }
};

</script>

<style scoped>
.people-conatainer {
    display: flex;
    position: absolute;
    right: 15vw;
    top: 66vh;
    width: 70vw;
    justify-content: space-between;
}

@keyframes arc {
    0% {
        transform: translate(0, 0);
    }
    50% {
        transform: rotate(10deg) translate(15vw, -15vh);  
    }
    100% {
        transform: rotate(10deg) translate(32vw, -10vh);  
    }
}

.box-animation {
  position: absolute;
  right: 62vw;
  top: 74vh;
  height: 10vh;
  width: 8vw;
  animation: arc 2.5s 1 linear forwards;
}

#arrow {
    position: absolute;
    right: 28vw;
    top: 65vh;
    height: 15vh;
    width: 36vw;
}
</style>
