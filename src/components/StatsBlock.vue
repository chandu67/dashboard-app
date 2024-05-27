<template>
  <div class="stats-card">
    <div class="card-header">
      <span class="card-title">{{ title }}</span>
      <div class="card-icon">
        <svg enable-background="new 0 0 30 30" height="30" viewBox="0 0 100 100" width="30"
          xmlns="http://www.w3.org/2000/svg">
          <path
            d="m79.5 74.1-16.6-16.5c3.4-4.7 5.1-10.7 4.2-17.1-1.5-10.7-10.2-19.2-21.1-20.2-14.7-1.5-27.2 11-25.7 25.8 1 10.7 9.5 19.6 20.2 21.1 6.4.9 12.3-.9 17.1-4.2l16.6 16.6c.7.7 1.9.7 2.6 0l2.6-2.6c.8-.9.8-2.1.1-2.9zm-51.8-30.4c0-8.8 7.2-16.1 16.1-16.1s16.1 7.2 16.1 16.1-7.2 16.1-16.1 16.1-16.1-7.1-16.1-16.1z"
            fill="#5ab5c6" />
        </svg>
      </div>
    </div>
    <div class="card-body">
      <span class="card-value">{{ value }}</span>
    </div>
    <div class="card-footer">
      <span :class="{ 'positive': isPositive, 'negative': !isPositive }">
        <span class="arrow" :class="{ 'up': isPositive, 'down': !isPositive }"></span>
        {{ percentage }} %
      </span>
      <span class="footer-label">{{ footerLabel }}</span>
    </div>
  </div>
</template>

<script setup>
import { defineProps, computed } from 'vue'

const props = defineProps({
  title: {
    type: String,
    required: true
  },
  value: {
    type: Number,
    required: true
  },
  icon: {
    type: String,
    required: true
  },
  percentage: {
    type: Number,
    required: true
  },
  footerLabel: {
    type: String,
    required: true
  }
})

const isPositive = computed(() => props.percentage >= 0)
</script>

<style scoped>
.stats-card {
  border-radius: 10px;
  padding: 20px;
  background-color: #fff;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  text-align: left;
  width: 250px;
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.card-title {
  font-size: 16px;
  font-weight: bold;
}

.card-icon {
  width: 35px;
  height: 35px;
  background-color: #dbecf2;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.card-body {
  margin-top: 10px;
  font-size: 36px;
  font-weight: bold;
}

.card-footer {
  margin-top: 10px;
  display: flex;
  align-items: center;
}

.card-footer .positive {
  color: #82c49e;
  font-weight: 700;
}

.card-footer .negative {
  color: red;
}

.footer-label {
  margin-left: 5px;
  color: #888;
  font-size: small;
  font-weight: 600;
}

.arrow {
  display: inline-block;
  width: 0;
  height: 0;
  margin-right: 5px;
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
}

.arrow.up {
  border-bottom: 10px solid green;
}

.arrow.down {
  border-top: 10px solid red;
}
</style>
