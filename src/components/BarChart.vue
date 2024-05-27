<template>
  <div id="bar-chart" class="pure-u-1 pure-u-md-1">
    <div class="heading">Recent Marketing</div>
    <div>
      <div>
        <span :class="{ 'positive': isPositive, 'negative': !isPositive }">
          <span class="arrow" :class="{ 'up': isPositive, 'down': !isPositive }"></span>
          {{ percentage }} %
        </span>
      </div>
      <div>
        <Bar :data="chartData" :options="chartOptions" :chart-id="chartId" :width="width" :height="height"
          :css-classes="cssClasses" :styles="styles" :plugins="plugins" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import { Bar } from 'vue-chartjs';
import { defineProps } from 'vue'
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale
} from 'chart.js';

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale);

const chartId = 'bar-chart';
const width = 400;
const height = 200;

const chartData = ref({
  labels: [
    "Jan",
    "Feb",
    "Mar",
    "Apr",
    "May",
    "Jun",
    "Jul",
    "Aug",
    "Sepr",
    "Oct",
    "Nov",
    "Dec"
  ],
  datasets: [
    {
      label: '',
      backgroundColor: '#0c97bb',
      data: [10, 20, 12, 40, 20, 12, 25, 39, 35, 39, 60, 71]
    }
  ]
});
const props = defineProps({
  percentage: {
    type: Number,
    required: true
  },
});

const isPositive = computed(() => props.percentage >= 0);

const chartOptions = {
  responsive: true,
  maintainAspectRatio: false
};

const cssClasses = '';
const styles = {};
const plugins = [];

</script>

<style scoped>
#bar-chart {
  background-color: white;
  border-radius: 20px;
  border: none;
  padding: 20px;
}

.positive {
  color: #82c49e;
  font-weight: 800;
}

.negative {
  color: red;
  font-weight: 800;
}

.arrow {
  display: inline-block;
  width: 0;
  height: 0;
  color: #82c49e;
  margin-right: 5px;
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
}

.arrow.up {
  border-bottom: 10px solid #82c49e;
}

.arrow.down {
  border-top: 10px solid red;
}

.heading {
  font-weight: 800;
  font-size: 15px;
}
</style>
