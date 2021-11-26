<template>
  <div @click="onColor(pixel.id)" :style="{ background: pixel.color }"></div>
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
