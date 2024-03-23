<template>
  <div>
    <h2>User Feedback</h2>
    <column-chart :data="formattedData" :library="{responsive: true}" />
  </div>
</template>

<script setup>

const props  = defineProps(['data'])
const formattedData = props.data.map(item => [item.제품, item.점수]);
</script>

<style scoped>


</style>
