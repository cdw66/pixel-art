<template>
  <div>
    <!-- <div :key="swatch.id" v-for="swatch in swatches"> -->
    <ColorSwatch
      @select-color="$emit('select-color', swatch.id)"
      :key="swatch.id"
      v-for="swatch in swatches"
      :swatch="swatch"
    />
    <!-- </div> -->
  </div>
</template>

<script>
import ColorSwatch from "./ColorSwatch.vue";

export default {
  name: "Color Picker",
  components: {
    ColorSwatch,
  },
  props: {
    swatches: Array,
  },
  emits: ["select-color"],
};
</script>

<style scoped>
div {
  display: flex;
  /* flex-direction: row; */
  border-style: solid;
  border-radius: 10px;
  border-width: 1px;
}
</style>