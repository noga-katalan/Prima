<template>
   <div id="snapshot-explanation">
         <h1 :class="{ 'side-title': page >= 5 && page < 8 }">לורם איפסום</h1>
         <img class="line" :class="{ 'side-line': page >= 5 && page < 8 }" src="../assets/images/line.png" alt="line">
         <h2 v-if="page<5">אז מה זה בעצם?</h2>
         <h2 v-if="page>=5 && page<8" :class="{ 'side-second-title': page >= 5 && page < 8 }">איך  עובד?</h2>
         <h2 v-if="page>=8">איך ניצור אותם?</h2>
         <p class="expScreen" :class="{ 'side-text': page >= 5 && page < 8 }">{{ text }}</p>
          <charts v-if="page===6 || page===7" :page="page"></charts> 
          <snapshot-example v-if="page ===5"></snapshot-example>
   </div>
</template>

<script>
import Charts from "@/components/Charts.vue"
import SnapshotExample from "@/components/SnapshotExample.vue"

export default {
   name: "snapshot-explanation",
   components : {
    Charts,
    SnapshotExample
   },
   props: ["text", "page"],
   data() {
     return {};
   },
   methods: {}
};
</script>

<style scoped>
#snapshot-explanation {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  text-align: center;
}

.expScreen {
  position: absolute;
  width: 60vw;
  font-size: 3vh;
  color: white;
  margin-top: 10vh;
  z-index: 3;
}

.side-text {
  text-align: right;
  position: absolute;
  top: 30vh;
  right: 7vw;
  font-size: 2.3vh;
  width: 43vw;
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

.line {
  position: absolute;
  top: 32vh;
  width: 30vw;
}

.side-title, .side-second-title, .side-line  {
  right: 7vw;
}

.side-line {
  width: 17vw ;
}

</style>
