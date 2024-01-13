<template>
  <div id="file-drag">
    <img v-if="!closedBox" @drop="drop" @dragover="allowDrop" class="box" src="../assets/images/openBox.png" alt="openBox"/>
    <img v-if="closedBox && !compressBox" class="box" src="../assets/images/closedBox.png" alt="closedBox"/>
    <img v-if="compressBox" id="compressed-box" class="box" src="../assets/images/closedBox.png" alt="closedBox"/>
    <div v-if="filesLeft != 0"> 
       <img draggable="true" @dragstart="drag" class="file" id="file1" src="../assets/images/yellowFile.png" alt="yellowFile">
        <img draggable="true" @dragstart="drag" class="file" id="file2" src="../assets/images/yellowFile.png" alt="yellowFile">
        <img draggable="true" @dragstart="drag" class="file" id="file3" src="../assets/images/yellowFile.png" alt="yellowFile">
        <img draggable="true" @dragstart="drag" class="file" id="file4" src="../assets/images/yellowFile.png" alt="yellowFile">
        <img draggable="true" @dragstart="drag" class="file" id="file5" src="../assets/images/yellowFile.png" alt="yellowFile">
        <img draggable="true" @dragstart="drag" class="file" id="file6" src="../assets/images/yellowFile.png" alt="yellowFile">
    </div>
    <p v-if="!closedBox" id="instruction">גררו את כל הקבצים לקופסא!</p>
    <p v-if="!closedBox" id="files-num">קבצים שנשארו: {{filesLeft}}</p>
    <button @click="compressBox = true" v-if="closedBox && !compressBox" id="compress-btn" class="custom-btn btn-5"><span>דחס</span></button>

    <h1 v-if="compressBox">Tape archive</h1>
    <img v-if="compressBox" id="line" src="../assets/images/line.png" alt="line">   
    <p v-if="compressBox" id="expScreen">לורם איפסום.,</p>

  </div>
</template>
 
<script>
export default {
    name: "file-drag",
    props: [""],
  data() {
    return {
        filesLeft: 6,
        closedBox: false,
        compressBox: false
    };
  },
  methods : {
    allowDrop(ev) {
      ev.preventDefault();
    },
    drag(ev) {
      ev.dataTransfer.setData("text", ev.target.id);
    },
    drop(ev) {
    this.filesLeft--;
    if (this.filesLeft === 0) {
        this.closedBox = true;
    }
      ev.preventDefault();
      let data = ev.dataTransfer.getData("text");
      ev.target.appendChild(document.getElementById(data));
    }
  },
};

</script>

<style scoped>
.box {
    width: 40vw;
    background: none;
    position: absolute;
    top: 32vh;
    left: 30vw;
}

.file {
    width: 7vw;
    position: absolute;
}

#file1 {
    top: 20vh;
    left: 20vw;
}

#file2 {
    top: 55vh;
    left: 13vw;
}

#file3 {
    top: 85vh;
    left: 20vw;
}

#file4 {
    top: 20vh;
    right: 20vw;
}

#file5 {
    top: 55vh;
    right: 13vw;
}

#file6 {
    top: 85vh;
    right: 20vw;
}

#instruction {
    position: absolute;
    bottom: 7vh;
    left: 37vw;
    color: white;
    font-size: 3.5vh;
}

#files-num {
    position: absolute;
    bottom: 5vh;
    color: white;
    font-size: 2.3vh;
    left: 44vw;
}

#compress-btn {
    position: absolute;
    bottom: 7vh; 
    left: 44vw;
}

#compressed-box {
    animation: compressAnimation 3s ease-in-out forwards;
}

@keyframes compressAnimation {
    0% {
        width: 40vw;
        transform: translate();
    }
    100% {
        width: 20vw;
        transform: translate(120px,100px);
    }
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

.btn-5 {
  background: #ffa827;
  line-height: 42px;
  padding: 0;
  border: none;
}
.btn-5:hover{
  background: transparent;
  color: #ffa827;
}
.btn-5:before,
.btn-5:after{
  content:'';
  position:absolute;
  top:0;
  right:0;
  height:2px;
  background: #ffa827;
  width:0;
    box-shadow:  0 0 5px #ffa827,  0 0 5px #ffa827 inset;
  transition:400ms ease all;
}
.btn-5:after{
  right:inherit;
  top:inherit;
  left:0;
  bottom:0;
}
.btn-5:hover:before,
.btn-5:hover:after{
  width:100%;
  transition:800ms ease all;
}

h1 {
    font-size: 6vh;
    color: white;
    font-weight: 700;
    position: absolute;
    top: 23vh;
    left: 38vw;
    animation: fadeInAnimation 2s ease-out forwards;
}

#line {
    position: absolute;
    top: 32vh;
    left: 34vw;
    width: 30vw;
    animation: fadeInAnimation 2s ease-out forwards;
}

#expScreen {
    position: relative;
    width: 60vw;
    font-size: 3vh;
    color: white;
    margin-top: 10vh;
    top: 25vh;
    animation: fadeInAnimation 2s ease-out forwards;
}

@keyframes fadeInAnimation {
    0% {
        transform: translateY(-40px);
        opacity: 0;
    }
    100% {
        transform: translateY(0px);
        opacity: 1;
    }
}

</style>
