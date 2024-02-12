<template>
  <div class="dashboard">
    <h1>Distributors Metrics</h1>
    <select v-model="selectedDistributorId">
      <option disabled value="">Please select Distributor</option>
      <option v-for="distributor in distributors" :key="distributor.id" :value="distributor.id">
        {{ distributor.name }}
      </option>
    </select>

    <div v-if="selectedDistributor" class="distributor-details">
      <h2>{{ selectedDistributor.name }}</h2>
      <p>Goods shipped last month: {{ selectedDistributor.lastMonthShipment }}</p>
      <p>Forecasted goods to ship next month: {{ selectedDistributor.forecastNextMonth }}</p>
      <p>Year-to-date average: {{ selectedDistributor.ytdAverage }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Dashboard',
  data() {
    return {
      selectedDistributorId: '',
      distributors: [
        { id: 1, name: 'Distributor A', lastMonthShipment: 100, forecastNextMonth: 120, ytdAverage: 110 },
        { id: 2, name: 'Distributor B', lastMonthShipment: 150, forecastNextMonth: 130, ytdAverage: 140 },
        { id: 3, name: 'Distributor C', lastMonthShipment: 200, forecastNextMonth: 180, ytdAverage: 190 },
      ],
    };
  },
  computed: {
    selectedDistributor() {
      return this.distributors.find(distributor => distributor.id === this.selectedDistributorId);
    }
  },
};
</script>

<style>
.dashboard {
  max-width: 600px;
  margin: auto;
  text-align: center;
}

.distributor-details {
  margin-top: 20px;
  border: 1px solid #eee;
  padding: 20px;
}

select {
  margin-top: 20px;
  padding: 10px;
  font-size: 16px;
}
</style>
