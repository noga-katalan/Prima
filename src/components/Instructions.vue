<template>
  <div id="instructions">
    <div class="background-container ">
        <h1>כל הכבוד! עכשיו כשאתם יודעים איך לשחזר את הקבצים, הגיע הזמן ליישם!</h1>
        <p id="text">במשחק הבא, עליכם להציל את הקבצים האבודים שעומדים להמחק. כדי לעשות זאת, יש לכם זמן מוגבל לשמור אותם בסנפשוט באמצעות מענה נכון על השאלות וכתיבת הפקודות המתאימות לפני שימחקו.</p>
        <button @click="$emit('start-game', 1)">מוכנים!</button>
    </div>
    
  </div>
</template>
 
<script>
export default {
    name: "instructions",
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
#instructions {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  text-align: center;
}

h1 {
    font-size: 4vh;
    width: 40vw;
    color: white;
    font-weight: 700;
    position: absolute;
    top: 10vh;
    right: 15vw;
}
#text {
    position: absolute;
    width: 42vw;
    font-size: 3vh;
    color: white;
    margin-top: 10vh;
    top: 23vh;
    right: 15vw;
}
.background-container {
    background-image: url(/img/gradientBackground.767ea25a.png);
    background-size: 100% 100%;
    width: 70vw;
    height: 77vh;
    position: absolute;
    top: 16vh;
    right: 16vw;
    display: inline-block;
    border-radius: 60px;
    border-style: outset;
}
button {
    position: absolute;
    top: 61vh;
    right: 30vw;
    height: 5vh;
    width: 12vw;
    background: gray;
    border-radius: 10px;
}
</style>
