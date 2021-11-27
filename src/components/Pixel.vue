<template>
  <!-- <div @click="onColor(pixel.id)" :style="{ background: pixel.color }"></div> -->
  <!-- <div
    @mouseover="onColor(pixel.id)"
    :style="{ background: pixel.color }"
  ></div> -->
  <div
    @mousedown="startColor()"
    @mouseover="onColor(pixel.id)"
    @mouseup="stopColor()"
    :style="{ background: pixel.color }"
  ></div>
</template>

<script>
export default {
  name: "Pixel",
  props: {
    pixel: Object,
  },

  methods: {
    onColor(id) {
      this.$emit("color-pixel", id);
      // this.$emit("start-color");
      // this.$emit("stop-color");
    },
    startColor() {
      this.$emit("start-color");
    },
    stopColor() {
      this.$emit("stop-color");
    },
  },
};
</script>

<style scoped>
div {
  height: 100%;
  width: 100%;
  /* display: flex; */
  border-style: solid;
  border-width: 1px;
}
</style>
