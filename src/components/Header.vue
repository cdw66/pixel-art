<template>
  <header>
    <h1>Pixel Art Maker</h1>
    <Button @click="onClear()" text="Clear" color="red" />
  </header>
</template>

<script>
import Button from "./Button.vue";

export default {
  name: "Header",
  components: {
    Button,
  },
  methods: {
    onClear() {
      // this.pixels.forEach((pixel) => (pixel.color = "white"));
      // console.log("clear");
      this.$emit("clear");
    },
  },
  emits: ["clear"],
};
</script>
<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  font-family: Arial, Helvetica, sans-serif;
}
</style>