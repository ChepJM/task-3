<template>
  <div class="dashboard">
    <div class="first-row">
      <div class="sales-feedback">
        <SalesData :data="sData"/>
        <UserFeedback :data="fData"/>
      </div>
    </div>
    <div class="second-row">
      <PerformanceIndicators :data="pData"/>
    </div>
  </div>
</template>

<script setup>
import {ref} from 'vue';
import SalesData from './components/SalesData.vue';
import UserFeedback from './components/UserFeedback.vue';
import PerformanceIndicators from './components/PerformanceIndicators.vue';

const sData = ref([
  {month: '1월', 제품A: 120, 제품B: 150, 제품C: 80},
  {month: '2월', 제품A: 200, 제품B: 180, 제품C: 160},
  {month: '3월', 제품A: 150, 제품B: 210, 제품C: 190}
]);
const fData = ref([
  {제품: '제품A', 점수: 4.5},
  {제품: '제품B', 점수: 4.7},
  {제품: '제품C', 점수: 4.3}
]);
const pData = ref([
  {제품: '제품A', 배터리수명: '10시간', 처리속도: '빠름'},
  {제품: '제품B', 배터리수명: '12시간', 처리속도: '보통'},
  {제품: '제품C', 배터리수명: '8시간', 처리속도: '느림'}
]);

</script>

<style scoped>
.dashboard {
  height: 100vh;
  display: flex;
  flex-direction: column;
  gap: 20px;
  background-color: rgba(13, 19, 18, 0.11);
}

.first-row {
  width: 100%;
}

.sales-feedback {
  width: 100%;
  display: flex;
  justify-content: space-around;
  gap: 20px;
}

.second-row {
  width: 100%;
}
</style>
