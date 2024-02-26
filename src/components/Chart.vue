<script lang="ts">
import { ref, onMounted } from 'vue';

import 'anychart';

export default {
  name: 'BusinessGraphics',
  setup() {
    const chart = ref<any>(null);
    onMounted(() => {
      if (chart.value !== null && chart.value !== undefined) {
        chart.value.dispose();
        chart.value = null;
      }
      anychart.onDocumentReady(() => {
        const data = {
          chart: {
            type: 'pie',
            data: [
              ['Chocolate', 5],
              ['Rhubarb compote', 2],
              ['Crêpe Suzette', 2],
              ['American blueberry', 2],
              ['Buttermilk', 1]
            ],
            container: 'anychart-container-id'
          }
        };

        chart.value = anychart.fromJson(data);
        chart.value.draw();
      });
    });
  }
};
</script>

<template>
  <div id="anychart-container-id" class="anychart-container"></div>
</template>

<style scoped>
.anychart-container {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
