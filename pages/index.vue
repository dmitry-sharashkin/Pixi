<template>
  <div></div>
</template>

<script>
import * as PIXI from "pixi.js";
import { arr } from "../constanst/segments";

export default {
  name: "IndexPage",
  data: function () {
    return {
      segmentsPos: [],
    };
  },
  mounted() {
    console.log(arr);
    // this.drawPixi();
    this.mapSegments();
    console.log(this.segmentsPos);
  },

  methods: {
    drawPixi() {},
    mapSegments() {
      this.segmentsPos = arr.map((s, index) => {
        if (index < 20) {
          return;
        }
        let letr = s.coordinates.match(/[a-zA-Z]+/g);
        let YNum = s.coordinates.match(/\d+/g);
        YNum = YNum.join("");

        let symbolsMap = {
          A: "0",
          B: "1",
          C: "2",
          D: "3",
          E: "4",
          F: "5",
          G: "6",
          H: "7",
          I: "8",
          J: "9",
          K: "10",
          L: "11",
          M: "12",
          N: "13",
          O: "14",
          P: "15",
          Q: "16",
          R: "17",
          S: "18",
          T: "19",
          U: "20",
          V: "21",
          W: "22",
          X: "23",
          Y: "24",
          Z: "25",
        };

        let letrToNum = letr.map((l) => {
          let numbers = l.replace(
            /./gi,
            ($0) => symbolsMap[$0.toUpperCase()] || $0
          );
          return +numbers;
        });

        let xPos = letrToNum.reduce((prev, cur) => prev + cur, 0);
        s.coordinates = { x: xPos, y: +YNum };
        return s;
      });
    },
  },
};
</script>
<style></style>
