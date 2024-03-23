<template>
  <div>
    <h2>Sales Data</h2>

    <line-chart :data="formattedData" :library="{responsive: true}" />
  </div>
</template>

<script setup>

const props  = defineProps(['data'])
const formattedData = Object.entries(props.data).map(([month, sales]) => ({ name: month, data: sales }));
</script>

<style scoped>


</style>
