<script setup>
import Plotly from 'plotly.js-dist';
import { ref, onMounted } from 'vue';

const TESTER = ref("tester");
console.log(TESTER.value);

onMounted(() => {
  const metrics_across_thresholds = fetch("assets/metrics_across_thresholds.json").json();
  console.log(metrics_across_thresholds);
  console.log("wtf")

  Plotly.newPlot(TESTER.value, [{
    x: [1, 2, 3, 4, 5],
    y: [1, 2, 4, 8, 16]
  }], {
    margin: { t: 0 }
  });
});
</script>

<template>
  <div id="tester" :ref="TESTER" style="width: 600px; height: 250px;"> Hello </div>
</template>