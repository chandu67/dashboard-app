<template>
  <div class="line-chart pure-u-1 pure-u-md-1">
    <div class="heading">Recent Workflow</div>
    <div>
      <div>
        <span :class="{ 'positive': isPositive, 'negative': !isPositive }">
          <span class="arrow" :class="{ 'up': isPositive, 'down': !isPositive }"></span>
          {{ percentage }} %
        </span>
      </div>
      <div class="canvas-chart">
        <canvas ref="canvas"></canvas>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, computed, defineProps } from 'vue';
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  LineElement,
  CategoryScale,
  LinearScale,
  PointElement
} from 'chart.js';

ChartJS.register(Title, Tooltip, Legend, LineElement, CategoryScale, LinearScale, PointElement);

const canvas = ref(null);
const chart = ref(null);

const props = defineProps({
  percentage: {
    type: Number,
    required: true
  },
});

const isPositive = computed(() => props.percentage >= 0);

const chartData = ref({
  labels: [
    "Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"
  ],
  datasets: [
    {
      label: "",
      data: [2, 10, 5, 9, 0, 6, 20, 2, 28, 3, 19, 5],
      backgroundColor: '#0c97bb',
      borderColor: '#0c97bb',
      pointBackgroundColor: "#fff",
      tension: 0.4,
    },
  ],
});

const chartOptions = {
  responsive: true,
  maintainAspectRatio: false,
  title: {
    display: true,
    text: "My Data",
  },
};


onMounted(() => {
  const ctx = canvas.value.getContext('2d');
  chart.value = new ChartJS(ctx, {
    type: 'line',
    data: chartData.value,
    options: chartOptions,
  });
});
</script>

<style scoped>
.line-chart {
  background-color: white;
  border-radius: 20px;
  border: none;
  padding: 20px;
}

.canvas-chart {
  height: 200px;
  width: 400px;
  max-height: 100vh;
  overflow: hidden;

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
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  margin-right: 5px;
}

.up {
  border-bottom: 10px solid #82c49e;
}

.down {
  border-top: 10px solid red;
}

.heading {
  font-weight: 800;
  font-size: 15px;
}
</style>
