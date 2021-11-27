<template>
  <div :key="pixel.id" v-for="pixel in pixels">
    <!-- <Pixel @color-pixel="$emit('color-pixel', pixel.id)" :pixel="pixel" /> -->
    <Pixel
      @start-color="$emit('start-color')"
      @color-pixel="$emit('color-pixel', pixel.id)"
      @stop-color="$emit('stop-color')"
      :pixel="pixel"
    />
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
  emits: ["start-color", "stop-color", "color-pixel"],
};
</script>

<style scoped>
</style>
