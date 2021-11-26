<template>
  <div :key="pixel.id" v-for="pixel in pixels">
    <Pixel @color-pixel="$emit('color-pixel', pixel.id)" :pixel="pixel" />
  </div>
</template>

<script>
import Pixel from "./Pixel.vue";

export default {
  name: "Grid",
  components: {
    Pixel,
  },
  props: {
    pixels: Array,
  },
  emits: ["color-pixel"],
};
</script>

<style scoped>
</style>
