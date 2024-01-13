<template>
  <div id="snapshot-example">
    <!-- <img v-if="showCloudDay1" id="cloud-day-1" src="../assets/images/SnapshotDay1.png" alt="SnapshotDay1"/>
    <img v-if="!showCloudDay1" class="fade" id="cloud-day-1" src="../assets/images/SnapshotDay1.png" alt="SnapshotDay1"/>
    <img v-if="!showCloudDay1" id="cloudDay1Changed" class="cloudsSecondPart" src="../assets/images/SnapshotDay1Changed.png"/>
    <img v-if="!showCloudDay1" id="cloudDay2" class="cloudsSecondPart" src="../assets/images/SnapshotDay2.png"/> -->

    <div id="file1" class="file-container">
        <p class="file-name">קובץ 1</p>
    </div>
    <div v-if="showCloudDay1" id="file2" class="file-container">
        <p class="file-name">קובץ 2</p>
    </div>
    <div v-if="!showCloudDay1" id="file2" class="file-container moveFile">
        <p class="file-name">קובץ 2</p>
    </div>

    <button v-if="showCloudDay1" @click="playAnimation" id="delete-btn" type="button">מחק</button>
  </div>
</template>

<script>
export default {
  name: "snapshot-example",
  props: [""],
  data() {
    return {
        showCloudDay1: true
    };
  },
    methods: {
        playAnimation() {
            this.showCloudDay1 = false;
        }
    }
};
</script>

<style scoped>
    #snapshot-example {
        width: 40vw;
        height: 80vh;
        background-image: url("../assets/images/SnapshotExampleDiv.png");
        background-size: 100% 100%;
        position: absolute;
        left: 10vw;
        bottom: 5vh;
    }
    
    .moveFile {
       animation: moveFile 3s ease-in-out forwards; 
    }

    .cloudsSecondPart {
        animation: fadeInAnimation 2s ease-in forwards;
    }

    .cloudsSecondPart {
        width: 27vw;
        position: absolute;
    }

    #cloudDay1Changed {
        top: 1vh;
        left: -5vw;
    }

    #cloudDay2 {
        top: 12vh;
        right: -2vw;
    }

    .fade {
        animation: fadeOutAnimation 1s ease-in forwards;
    }

    #cloud-day-1 {
        width: 33vw;
        position: absolute;
        left: 3vw;
        top: 5vh;
    }

    .file-container {
        width: 9vw;
        height: 10vh;
        background-image: url("../assets/images/blueFile.png");
        background-size: 100% 100%;
        position: absolute;
        bottom: 13vh;
        right: 9vw;
    }

    #file2 {
        right: 22.5vw;
    }

    .file-name {
        border: none;
        font-weight: bold;
        color: white;
        position: relative;
        top: 4vh;
    }

    #delete-btn {
        position: absolute;
        bottom: 5vh;
        font-size: 2vh;
        font-weight: bold;
        padding: 10px 40px;
        border-radius: 10px;
        border: none;
        left: 15vw;
        background-color: rgb(219, 61, 61);
        color: white;
        transition: 0.3s;
        
    }

    #delete-btn:hover {
        cursor: pointer;
        background-color: rgb(189, 45, 45);
    }

    @keyframes moveFile {
        0% {
            transform: translate();
        }
        100% {
            transform: translate(-100px, -460px);
        }
    }

    @keyframes fadeInAnimation {
        100% {
            opacity: 1;
        }
        0% {
            opacity: 0;
        }
    }

    @keyframes fadeOutAnimation {
        0% {
            opacity: 1;
        }
        100% {
            opacity: 0;
        }
    }
</style>
