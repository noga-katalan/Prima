<template>
  <div id="nav-bar">
    <nav>
      <p class="item" :class="{ 'active': page >= 0 && page < 5 }" @click="selectItem('0')">S</p>
      <p class="item" :class="{ 'active': page >= 5 && page < 8 }" @click="selectItem('5')">פעולת</p>
      <p class="item" :class="{ 'active': selectedItem === '8' }" @click="selectItem('8')">יצירת </p>
      <p class="item" :class="{ 'active': page >= 9 && page < 12 }" @click="selectItem('9')">T</p>
      <p class="item" :class="{ 'active': selectedItem === '12' }" @click="selectItem('12')">חשיבות </p>
      <p class="item" :class="{ 'active': selectedItem === '13' }" @click="selectItem('13')">יצירת </p>
    </nav>
  </div>
</template>

<script>
export default {
  name: "nav-bar",
  props: ["page"],
  computed: {
    selectedItem() {
      return this.page.toString();
    },
  },
  methods: {
    selectItem(item) {
      this.$emit("update:page", Number(item));
    },
  },
};
</script>

<style scoped>
nav {
  position: absolute;
  top: 3vh;
  width: 90%;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
}

.item {
  font-size: 1.8vh;
  display: inline-block;
  color: white;
  padding: 0 30px;
  cursor: pointer;
}

.active {
  background-color: white;
  color: black;
  font-weight: bold;
  padding: 7px 25px;
  border-radius: 20px;
}

.active:hover {
  box-shadow: 6px 7px 7px -6px rgba(255, 255, 255, 0.61);
}
</style>

