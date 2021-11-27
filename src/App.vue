<template>
  <div class="container">
    <Header @clear="clearGrid" />
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
</template>

<script>
// import Header from './components/Header'
import Header from "./components/Header.vue";
// import Pixel from "./components/Pixel.vue";
import Grid from "./components/Grid.vue";

export default {
  name: "App",
  components: {
    Header,
    Grid,
    // Pixel,
  },
  data() {
    return {
      mouseDown: false,
      pixels: [],
    };
  },
  methods: {
    colorPixel(id) {
      if (this.mouseDown) {
        this.pixels.forEach((pixel) => {
          if (pixel.id == id) {
            pixel.color = "black";
          }
        });
      }
    },

    startColor() {
      this.mouseDown = true;
      console.log("mouse is down!");
      console.log(this.mouseDown);
    },

    stopColor() {
      this.mouseDown = false;
      console.log(this.mouseDown);
      console.log("mouse is up!");
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
</style>;
