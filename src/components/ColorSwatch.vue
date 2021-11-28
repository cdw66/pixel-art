<template>
  <div @click="onSelect(id)" :style="{ background: swatch.color }"></div>
</template>

<script>
export default {
  name: "Color Swatch",
  props: {
    swatch: Object,
  },
  methods: {
    onSelect(id) {
      this.$emit("select-color", id);
    },
  },
};
</script>

<style scoped>
div {
  width: 30px;
  height: 30px;
  margin: 10px;
}
</style>