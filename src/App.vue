<template>
  <div id="app">
    <div class="pure-g main-content">
      <!-- Sidebar -->
      <div class="pure-u-1 pure-u-md-1-5 sidebar">
        <NavBar />
      </div>
      <!-- Main Content -->
      <div class="pure-u-1 pure-u-md-4-5">
        <div class="pure-g overview">
          <div class="pure-u-1 pure-u-md-2-4">
            <h1>Overview</h1>
          </div>
          <div class="pure-u-1 pure-u-md-1-4">

            <div class="pure-g admin">
              <div class="item-icon"></div>
              <div class="dropdown">
                <select class="admin-select">
                  <option value="weekly">Administrator</option>
                  <option value="monthly">Logout</option>
                </select>
              </div>
            </div>
          </div>
        </div>
        <div class="pure-g content">
          <div class="pure-u-1 pure-u-md-3-4">
            <div class="pure-g stats-overview">
              <div class="pure-u-1 pure-u-md-1-3">
                <StatsBlock title="Document" :value="146.000" icon="path/to/icon.png" :percentage="17"
                  footerLabel="Since last week" />
              </div>
              <div class="pure-u-1 pure-u-md-1-3">
                <StatsBlock title="Contact" :value="1400" icon="path/to/icon.png" :percentage="17"
                  footerLabel="Since last week" />
              </div>
              <div class="pure-u-1 pure-u-md-1-3">
                <StatsBlock title="Email" :value="150.700" icon="path/to/icon.png" :percentage="17"
                  footerLabel="Since last week" />
              </div>
            </div>
            <div class="pure-g charts">
              <div class="pure-u-1 pure-u-md-1-2">
                <LineChart :percentage="17" />
              </div>
              <div class="pure-u-1 pure-u-md-1-2">
                <BarChart :percentage="17" />
              </div>
            </div>
            <div class="pure-g document-section">
              <div class="pure-u-1">
                <DocumentCard />
              </div>
            </div>
          </div>
          <!-- Chat bar -->
          <div class="pure-u-1 pure-u-md-1-4 chat-sidebar">
            <ChatBar />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BarChart from './components/BarChart.vue';
import LineChart from './components/LineChart.vue';
import StatsBlock from './components/StatsBlock.vue';
import DocumentCard from './components/DocumentCard.vue';
import NavBar from './components/NavBar.vue';
import ChatBar from './components/ChatBar.vue';

export default {
  name: 'App',
  components: {
    BarChart,
    LineChart,
    StatsBlock,
    DocumentCard,
    NavBar,
    ChatBar,
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  background-color: #f0f1f3;
}

.main-content {
  display: flex;
  flex-wrap: wrap;
}

.content {
  padding: 20px;
  display: flex;
  flex-wrap: wrap;
}

.overview {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
  margin: -10px 0 -40px 0;
  padding: 20px;
}

.stats-overview {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  padding: 10px 0;
}

.charts {
  display: flex;
  flex-wrap: wrap;
  gap: 30px;
  padding: 10px 0;
}

.document-section {
  margin-top: 20px;
}

.chat-sidebar {
  color: white;
  padding: 10px 20px;
  overflow-y: auto;
}

.admin {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
  padding-right: 20px;
}

.admin-select {
  background-color: #f0f1f3;
  border: none;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  width: 100%;
  max-width: 200px;
}

.dropdown select {
  padding: 5px 10px;
  border-radius: 5px;
  min-height: 30px;
  border: none;
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

.item-icon {
  width: 40px;
  height: 40px;
  background: #f38253;
  border-radius: 50%;
}
</style>
