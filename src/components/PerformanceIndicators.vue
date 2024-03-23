<template>
  <div class="performance-indicators">
    <h2>Performance Indicators</h2>
    <div v-if="data.length" class="chart-container">
      <div class="chart">
        <h3>Battery Life</h3>
        <column-chart :data="batteryLifeData" :library="{responsive: true}" />
      </div>
      <div class="chart">
        <h3>Processing Speed</h3>
        <column-chart :data="processingSpeedData" :library="{responsive: true}" />
      </div>
    </div>
    <div v-else>
      No data available
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  data: Array
});

// Extract battery life and processing speed data
const batteryLifeData = props.data.reduce((acc, item) => {
  acc[item.제품] = parseInt(item.배터리수명);
  return acc;
}, {});

const processingSpeedData = props.data.reduce((acc, item) => {
  acc[item.제품] = performanceToNumber(item.처리속도);
  return acc;
}, {});

// Helper function to convert performance speed to a numerical value
function performanceToNumber(speed) {
  switch (speed) {
    case '빠름':
      return 3;
    case '보통':
      return 2;
    case '느림':
      return 1;
    default:
      return 0;
  }
}
</script>

<style scoped>
.performance-indicators {
  height: 100%; /* Set the height of the container to 100% of the viewport height */
  overflow-y: auto; /* Add vertical scroll if content exceeds viewport height */
}

.chart-container {
  display: flex;
  flex-direction: row;
  gap: 20px; /* Add space between charts */
}

.chart {
  width: 100%; /* Ensure charts take full width of the container */
}
</style>