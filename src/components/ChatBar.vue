<template>
  <div class="sidebar-container">
    <div class="section">
      <h3>Popular Product</h3>
      <div v-for="(product, index) in products" :key="index" class="item">
        <div class="item-icon"></div>
        <div class="item-info">
          <p class="item-name">{{ product.name }}</p>
          <p class="item-price">{{ product.price }}</p>
        </div>
      </div>
    </div>
    <div class="section">
      <h3>Chat</h3>
      <div v-for="(chat, index) in chats" :key="index" class="item">
        <div class="item-icon"></div>
        <div class="item-info">
          <p class="item-name">{{ chat.name }}</p>
          <p class="item-message">{{ chat.message }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const products = ref([
  { name: 'Gadget Converter', price: '$250' },
  { name: 'Lens Camera', price: '$50' },
  { name: 'Airpods', price: '$100' },
  { name: 'Macbook', price: '$999' },
]);

const chats = ref([
  { name: 'Debra Young', message: "How's my product?" },
  { name: 'Dorothy Collins', message: 'How was the meeting' },
  { name: 'Chris Jordan', message: 'How employee performance' },
  { name: 'Denise Murphy', message: 'How was the meeting' },
]);
</script>

<style scoped>
.sidebar-container {
  padding: 20px;
  background: #fff;
  min-width: 230px;
  width: max-content;
  border-radius: 8px;
}

.section {
  margin-bottom: 20px;
}

.section h3 {
  margin-bottom: 10px;
  color: #333;
}

.item {
  display: flex;
  align-items: center;
  margin: 20px 0;
}

.item-icon {
  width: 40px;
  height: 40px;
  background: #000;
  border-radius: 50%;
  margin-right: 15px;
}

.item-info {
  display: flex;
  flex-direction: column;
}

.item-name {
  margin-bottom: 5px;
  margin-top: -5px;
  color: #000;
  font-weight: bold;
}

.item-price,
.item-message {
  margin: 0;
  color: #888;
  font-size: x-small;
}
</style>
