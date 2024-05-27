<template>
  <div class="document-table">
    <div class="table-header">
      <div class="title">
        <h2>Document</h2>
        <p>Document tracking information</p>
      </div>
      <div class="dropdown">
        <select v-model="selectedPeriod" class="custom-select">
          <option value="weekly">Weekly</option>
          <option value="monthly">Monthly</option>
        </select>
      </div>
    </div>
    <table>
      <thead>
        <tr>
          <th>Name</th>
          <th>File</th>
          <th>Category</th>
          <th>Author</th>
          <th class="status-heading">Status</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(document, index) in documents" :key="index">
          <td>{{ document.name }}</td>
          <td>{{ document.file }}</td>
          <td>{{ document.category }}</td>
          <td>{{ document.author }}</td>
          <td class="align-right">
            <span :class="['status', document.status.toLowerCase()]">
              {{ document.status }}
            </span>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const documents = ref([
  { name: 'Annual Report', file: 'PDF', category: 'Property', author: 'Diana Matthews', status: 'Send' },
  { name: 'Business Plan', file: 'WORD', category: 'Cryptocurrency', author: 'Philip James', status: 'Send' },
  { name: 'Marketing Tool', file: 'PDF', category: 'Content Creator', author: 'Amanda Ross', status: 'Pending' }
]);

const selectedPeriod = ref('weekly');
</script>

<style scoped>
.document-table {
  background-color: #f9f9f9;
  border-radius: 10px;
  padding: 20px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.table-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}

.table-header .title h2 {
  margin: 0;
  font-size: 24px;
}

.table-header .title p {
  margin: 0;
  color: #888;
}

.dropdown select {
  padding: 5px 10px;
  border-radius: 5px;
  min-height: 30px;
  border: none;
}

table {
  width: 100%;
  border-collapse: collapse;
}

thead th {
  text-align: left;
  border-bottom: 1px solid #ddd;
  padding-bottom: 10px;
}

tbody td {
  padding: 10px 0;
}

tbody tr:not(:last-child) td {
  border-bottom: 1px solid #ddd;
}

.status-heading {
  width: 50px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  text-align: left;
  color: #a9a9a9;
}

.status {
  padding: 5px 10px;
  border-radius: 5px;
  min-width: 60px;
  display: inline-block;
  color: #fff;
  font-size: small;
  text-align: center;
}

.status.send {
  background-color: #d3ebdf;
  color: #82bf99;
}

.status.pending {
  background-color: #f9d9c9;
  color: #e39d89;
}


.custom-select {
  background-color: #eff1f2;
  border: none;
  border-radius: 4px;
  font-size: 12px;
  font-weight: 700;
  cursor: pointer;
  width: 100%;
  max-width: 200px;
}

.custom-select::after {
  border: none;
}

.custom-select:focus {
  outline: none;
}

.align-right {
  text-align: right;
}
</style>
