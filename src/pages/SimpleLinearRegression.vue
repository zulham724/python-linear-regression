<template>
  <div class="q-ma-lg">
    <div class="q-mb-sm" v-for="(item, i) in items.slice(0, 5)" :key="i">
      <div class="text-caption">Nomer: {{ i + 1 }}</div>
      <div class="text-caption">Horse power: {{ item.x }}</div>
      <div class="text-caption">pricing: {{ item.y }}</div>
    </div>
    <hr />
    <div v-for="(item, i) in describe" :key="i">
      <div class="text-body1">{{ i }} :</div>
      <div class="q-pl-md text-body2" v-for="(cal, c) in item" :key="c">
        {{ c }}: {{ cal }}
      </div>
    </div>
    <hr />
    <canvas id="myChart" width="400" height="150"></canvas>
    <hr />
    <div class="text-body2">Nilai Korelasinya: {{ correlation }}</div>
    <div class="text-caption text-red" v-if="correlation > 0.7">
      Nilai korelasinya termasuk Tinggi
    </div>
    <div
      class="text-caption text-red"
      v-if="correlation > 0.5 && correlation < 0.7"
    >
      Nilai korelasinya termasuk Sedang
    </div>
    <div class="text-caption text-red" v-if="correlation < 0.5">
      Nilai korelasinya termasuk Rendah
    </div>
  </div>
</template>

<script>
import Chart from "chart.js";

export default {
  data() {
    return {
      options: {
        responsive: true,
        maintainAspectRatio: false,
      },
      datacollection: null,
      correlation: 0,
      describe: {
        x: {
          count: 0,
          mean: 0,
          std: 0,
          min: 0,
          max: 0,
        },
        y: {
          count: 0,
          mean: 0,
          std: 0,
          min: 0,
          max: 0,
        },
      },
      items: [
        {
          x: 111,
          y: 13495,
        },
        {
          x: 111,
          y: 16500,
        },
        {
          x: 154,
          y: 16500,
        },
        {
          x: 102,
          y: 13950,
        },
        {
          x: 115,
          y: 17450,
        },
        {
          x: 110,
          y: 15250,
        },
        {
          x: 110,
          y: 17710,
        },
        {
          x: 110,
          y: 18920,
        },
        {
          x: 140,
          y: 23875,
        },
        {
          x: 101,
          y: 16430,
        },
        {
          x: 101,
          y: 16925,
        },
        {
          x: 121,
          y: 20970,
        },
        {
          x: 121,
          y: 21105,
        },
        {
          x: 121,
          y: 24565,
        },
        {
          x: 182,
          y: 30760,
        },
        {
          x: 182,
          y: 41315,
        },
        {
          x: 182,
          y: 36880,
        },
        {
          x: 48,
          y: 5151,
        },
        {
          x: 70,
          y: 6295,
        },
        {
          x: 70,
          y: 6575,
        },
        {
          x: 68,
          y: 5572,
        },
        {
          x: 68,
          y: 6377,
        },
        {
          x: 102,
          y: 7957,
        },
        {
          x: 68,
          y: 6229,
        },
        {
          x: 68,
          y: 6692,
        },
        {
          x: 68,
          y: 7609,
        },
        {
          x: 88,
          y: 8921,
        },
        {
          x: 145,
          y: 12964,
        },
        {
          x: 58,
          y: 6479,
        },
        {
          x: 76,
          y: 6855,
        },
        {
          x: 60,
          y: 5399,
        },
        {
          x: 76,
          y: 6529,
        },
        {
          x: 76,
          y: 7129,
        },
        {
          x: 76,
          y: 7295,
        },
        {
          x: 76,
          y: 7295,
        },
        {
          x: 86,
          y: 7895,
        },
        {
          x: 86,
          y: 9095,
        },
        {
          x: 86,
          y: 8845,
        },
        {
          x: 86,
          y: 10295,
        },
        {
          x: 101,
          y: 12945,
        },
        {
          x: 100,
          y: 10345,
        },
        {
          x: 78,
          y: 6785,
        },
        {
          x: 90,
          y: 11048,
        },
        {
          x: 176,
          y: 32250,
        },
        {
          x: 176,
          y: 35550,
        },
        {
          x: 262,
          y: 36000,
        },
        {
          x: 68,
          y: 5195,
        },
        {
          x: 68,
          y: 6095,
        },
        {
          x: 68,
          y: 6795,
        },
        {
          x: 68,
          y: 6695,
        },
        {
          x: 68,
          y: 7395,
        },
        {
          x: 101,
          y: 10945,
        },
        {
          x: 101,
          y: 11845,
        },
        {
          x: 101,
          y: 13645,
        },
        {
          x: 135,
          y: 15645,
        },
        {
          x: 84,
          y: 8845,
        },
        {
          x: 84,
          y: 8495,
        },
        {
          x: 84,
          y: 10595,
        },
        {
          x: 84,
          y: 10245,
        },
        {
          x: 64,
          y: 10795,
        },
        {
          x: 84,
          y: 11245,
        },
        {
          x: 120,
          y: 18280,
        },
        {
          x: 72,
          y: 18344,
        },
        {
          x: 123,
          y: 25552,
        },
        {
          x: 123,
          y: 28248,
        },
        {
          x: 123,
          y: 28176,
        },
        {
          x: 123,
          y: 31600,
        },
        {
          x: 155,
          y: 34184,
        },
        {
          x: 155,
          y: 35056,
        },
        {
          x: 184,
          y: 40960,
        },
        {
          x: 184,
          y: 45400,
        },
        {
          x: 175,
          y: 16503,
        },
        {
          x: 68,
          y: 5389,
        },
        {
          x: 68,
          y: 6189,
        },
        {
          x: 68,
          y: 6669,
        },
        {
          x: 102,
          y: 7689,
        },
        {
          x: 116,
          y: 9959,
        },
        {
          x: 88,
          y: 8499,
        },
        {
          x: 145,
          y: 12629,
        },
        {
          x: 145,
          y: 14869,
        },
        {
          x: 145,
          y: 14489,
        },
        {
          x: 88,
          y: 6989,
        },
        {
          x: 88,
          y: 8189,
        },
        {
          x: 116,
          y: 9279,
        },
        {
          x: 116,
          y: 9279,
        },
        {
          x: 69,
          y: 5499,
        },
        {
          x: 55,
          y: 7099,
        },
        {
          x: 69,
          y: 6649,
        },
        {
          x: 69,
          y: 6849,
        },
        {
          x: 69,
          y: 7349,
        },
        {
          x: 69,
          y: 7299,
        },
        {
          x: 69,
          y: 7799,
        },
        {
          x: 69,
          y: 7499,
        },
        {
          x: 69,
          y: 7999,
        },
        {
          x: 69,
          y: 8249,
        },
        {
          x: 97,
          y: 8949,
        },
        {
          x: 97,
          y: 9549,
        },
        {
          x: 152,
          y: 13499,
        },
        {
          x: 152,
          y: 14399,
        },
        {
          x: 152,
          y: 13499,
        },
        {
          x: 160,
          y: 17199,
        },
        {
          x: 200,
          y: 19699,
        },
        {
          x: 160,
          y: 18399,
        },
        {
          x: 97,
          y: 11900,
        },
        {
          x: 95,
          y: 13200,
        },
        {
          x: 97,
          y: 12440,
        },
        {
          x: 95,
          y: 13860,
        },
        {
          x: 95,
          y: 15580,
        },
        {
          x: 95,
          y: 16900,
        },
        {
          x: 95,
          y: 16695,
        },
        {
          x: 95,
          y: 17075,
        },
        {
          x: 97,
          y: 16630,
        },
        {
          x: 95,
          y: 17950,
        },
        {
          x: 142,
          y: 18150,
        },
        {
          x: 68,
          y: 5572,
        },
        {
          x: 102,
          y: 7957,
        },
        {
          x: 68,
          y: 6229,
        },
        {
          x: 68,
          y: 6692,
        },
        {
          x: 68,
          y: 7609,
        },
        {
          x: 88,
          y: 8921,
        },
        {
          x: 145,
          y: 12764,
        },
        {
          x: 143,
          y: 22018,
        },
        {
          x: 207,
          y: 32528,
        },
        {
          x: 207,
          y: 34028,
        },
        {
          x: 207,
          y: 37028,
        },
        {
          x: 95,
          y: 9295,
        },
        {
          x: 95,
          y: 9895,
        },
        {
          x: 110,
          y: 11850,
        },
        {
          x: 110,
          y: 12170,
        },
        {
          x: 110,
          y: 15040,
        },
        {
          x: 110,
          y: 15510,
        },
        {
          x: 160,
          y: 18150,
        },
        {
          x: 160,
          y: 18620,
        },
        {
          x: 69,
          y: 5118,
        },
        {
          x: 73,
          y: 7053,
        },
        {
          x: 73,
          y: 7603,
        },
        {
          x: 82,
          y: 7126,
        },
        {
          x: 82,
          y: 7775,
        },
        {
          x: 94,
          y: 9960,
        },
        {
          x: 82,
          y: 9233,
        },
        {
          x: 111,
          y: 11259,
        },
        {
          x: 82,
          y: 7463,
        },
        {
          x: 94,
          y: 10198,
        },
        {
          x: 82,
          y: 8013,
        },
        {
          x: 111,
          y: 11694,
        },
        {
          x: 62,
          y: 5348,
        },
        {
          x: 62,
          y: 6338,
        },
        {
          x: 62,
          y: 6488,
        },
        {
          x: 62,
          y: 6918,
        },
        {
          x: 62,
          y: 7898,
        },
        {
          x: 62,
          y: 8778,
        },
        {
          x: 70,
          y: 6938,
        },
        {
          x: 70,
          y: 7198,
        },
        {
          x: 56,
          y: 7898,
        },
        {
          x: 56,
          y: 7788,
        },
        {
          x: 70,
          y: 7738,
        },
        {
          x: 70,
          y: 8358,
        },
        {
          x: 70,
          y: 9258,
        },
        {
          x: 70,
          y: 8058,
        },
        {
          x: 70,
          y: 8238,
        },
        {
          x: 112,
          y: 9298,
        },
        {
          x: 112,
          y: 9538,
        },
        {
          x: 116,
          y: 8449,
        },
        {
          x: 116,
          y: 9639,
        },
        {
          x: 116,
          y: 9989,
        },
        {
          x: 116,
          y: 11199,
        },
        {
          x: 116,
          y: 11549,
        },
        {
          x: 116,
          y: 17669,
        },
        {
          x: 92,
          y: 8948,
        },
        {
          x: 73,
          y: 10698,
        },
        {
          x: 92,
          y: 9988,
        },
        {
          x: 92,
          y: 10898,
        },
        {
          x: 92,
          y: 11248,
        },
        {
          x: 161,
          y: 16558,
        },
        {
          x: 161,
          y: 15998,
        },
        {
          x: 156,
          y: 15690,
        },
        {
          x: 156,
          y: 15750,
        },
        {
          x: 52,
          y: 7775,
        },
        {
          x: 85,
          y: 7975,
        },
        {
          x: 52,
          y: 7995,
        },
        {
          x: 85,
          y: 8195,
        },
        {
          x: 85,
          y: 8495,
        },
        {
          x: 68,
          y: 9495,
        },
        {
          x: 100,
          y: 9995,
        },
        {
          x: 90,
          y: 11595,
        },
        {
          x: 90,
          y: 9980,
        },
        {
          x: 110,
          y: 13295,
        },
        {
          x: 68,
          y: 13845,
        },
        {
          x: 88,
          y: 12290,
        },
        {
          x: 114,
          y: 12940,
        },
        {
          x: 114,
          y: 13415,
        },
        {
          x: 114,
          y: 15985,
        },
        {
          x: 114,
          y: 16515,
        },
        {
          x: 162,
          y: 18420,
        },
        {
          x: 162,
          y: 18950,
        },
        {
          x: 114,
          y: 16845,
        },
        {
          x: 160,
          y: 19045,
        },
        {
          x: 134,
          y: 21485,
        },
        {
          x: 106,
          y: 22470,
        },
        {
          x: 114,
          y: 22625,
        },
      ],
    };
  },
  mounted() {
    this.initChart();
    const x = this.items.map((item) => item.x);
    const y = this.items.map((item) => item.y);

    this.correlation = this.getCorrelation(this.items);

    this.describe.x = {
      ...this.describe.x,
      count: this.getCount(x),
      mean: this.getMean(x),
      std: this.getStandardDeviation(x),
      max: Math.max.apply(Math, x),
      min: Math.min.apply(Math, x),
    };

    this.describe.y = {
      ...this.describe.y,
      count: this.getCount(y),
      mean: this.getMean(y),
      std: this.getStandardDeviation(y),
      max: Math.max.apply(Math, y),
      min: Math.min.apply(Math, y),
    };
  },
  methods: {
    initChart() {
      var ctx = document.getElementById("myChart");
      const myChart = new Chart(ctx, {
        type: "scatter",
        data: {
          datasets: [
            {
              label: "# of Votes",
              data: this.items,
              backgroundColor: "red",
            },
          ],
        },
        options: {
          responsive: true,
        },
      });
    },
    getCorrelation(array = Array) {
      let n = array.length;
      let Σx = array.map((item) => item.x).reduce((a, b) => a + b, 0);

      let Σy = array.map((item) => item.y).reduce((a, b) => a + b, 0);

      let Σx2 = array.map((item) => item.x * item.x).reduce((a, b) => a + b, 0);

      let Σy2 = array.map((item) => item.y * item.y).reduce((a, b) => a + b, 0);

      let Σxy = array.map((item) => item.x * item.y).reduce((a, b) => a + b, 0);

      let r1 = n * Σxy - Σx * Σy;
      let r2 = n * Σx2 - Σx * Σx;
      let r3 = n * Σy2 - Σy * Σy;
      let r4 = Math.sqrt(r2 * r3);

      return r1 / r4;
    },
    getCount(array = Array) {
      let res = 0;
      array.forEach((item) => res += item);
      return res;
    },
    getMean(array = Array) {
      let total = 0;
      array.forEach((item) => total += item);
      return total / array.length;
    },
    getStandardDeviation(array = Array) {
      const n = array.length;
      const mean = array.reduce((a, b) => a + b) / n;
      return Math.sqrt(
        array.map((x) => Math.pow(x - mean, 2)).reduce((a, b) => a + b) / n
      );
    },
  },
};
</script>

<style>
</style>
