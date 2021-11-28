<template>
  <div class="container">
    <Header @clear="clearGrid" />
  </div>
  <div class="editor">
    <div>
      <ColorPicker @select-color="selectColor" :swatches="swatches" />
    </div>
    <div @mouseleave="stopColor" class="grid">
      <!-- <Grid @color-pixel="colorPixel" :pixels="pixels" /> -->
      <Grid
        @start-color="startColor"
        @color-pixel="colorPixel"
        @stop-color="stopColor"
        :pixels="pixels"
      />
    </div>
  </div>
</template>

<script>
// import Header from './components/Header'
import Header from "./components/Header.vue";
// import Pixel from "./components/Pixel.vue";
import Grid from "./components/Grid.vue";
import ColorPicker from "./components/ColorPicker.vue";

export default {
  name: "App",
  components: {
    Header,
    Grid,
    ColorPicker,
  },
  data() {
    return {
      mouseDown: false,
      selectedColor: "black",
      pixels: [],
      swatches: [],
    };
  },
  methods: {
    colorPixel(id) {
      if (this.mouseDown) {
        this.pixels.forEach((pixel) => {
          if (pixel.id == id) {
            pixel.color = this.selectedColor;
          }
        });
      }
    },

    startColor() {
      this.mouseDown = true;
    },

    stopColor() {
      this.mouseDown = false;
    },

    selectColor(id) {
      this.color = this.swatches.forEach((swatch) => {
        if (swatch.id == id) {
          this.selectedColor = swatch.color;
          console.log(this.selectedColor);
        }
      });
    },

    // generateGrid() {
    //   let blank = [];
    //   for (let i = 0; i < 64; i++) {
    //     let p = { id: i + 1, color: "white" };
    //     blank.push(p);
    //   }
    //   return blank;
    // },

    clearGrid() {
      let blank = [];
      let id = 1;
      for (let i = 0; i < 16; i++) {
        for (let j = 0; j < 16; j++) {
          let p = { id: id + 1, color: "white" };
          blank.push(p);
          id++;
        }
      }
      this.pixels = blank;
    },
  },

  created() {
    let blank = [];
    let id = 1;
    for (let i = 0; i < 16; i++) {
      for (let j = 0; j < 16; j++) {
        let p = { id: id + 1, color: "white" };
        blank.push(p);
        id++;
      }
    }

    this.pixels = blank;

    this.swatches = [
      {
        id: 1,
        color: "red",
      },
      {
        id: 2,
        color: "green",
      },
      {
        id: 3,
        color: "blue",
      },
      {
        id: 4,
        color: "black",
      },
    ];

    // this.pixels = [
    //   {
    //     id: 1,
    //     color: "white",
    //   },
    //   {
    //     id: 2,
    //     color: "white",
    //   },
    //   {
    //     id: 3,
    //     color: "white",
    //   },
    // ];
  },
};
</script>

<style>
.grid {
  display: grid;

  grid-template-rows: repeat(16, 1fr);
  grid-template-columns: repeat(16, 1fr);

  width: 400px;
  height: 400px;
  margin: auto;
}

.btn {
  padding: 10px;
  border-radius: 5px;
  border-style: none;
  font-weight: bold;
}

.editor {
  display: flex;
}
</style>;
