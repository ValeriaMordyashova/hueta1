<script setup>
import BlockCurrent from "./BlockСurrent.vue"
</script>

<template>
  <div>
    <div v-if="error">{{ error }}</div>
    <div v-else>
      <div class="block_select center">
        <script>
        // From any currency, to any currency:
        fx.convert(12.99, {from: "GBP", to: "HKD"});
        </script>
        <h2>Выберете валюту</h2>
        <select v-model="baseCurrency" @change="fetchRates">
          <option v-for="(rate, currency) in rates" :key="currency" :value="currency" >{{ currency }}</option>
        </select>
      </div>
      <br><br>
      <h1>{{ baseCurrency }}</h1>
      <div class="wrapper"> <!-- попробовать вывести всё это через доп компонент -->
          <div v-for="(rate, currency) in rates" :key="currency" class="item">
            <!-- <img />  попробовать еще впихнуть сюда флаг страны-->
            <h3>{{ currency }}</h3>
            <p>{{ rate }}</p>
          </div>
      </div>
    </div>
  </div>
</template>

<script>
// import axios from 'axios';

// export default {
//   data() {
//     return {
//       apiKey: '12de564a6bde4bb6a1cf3ca31e430e86',
//       baseCurrency: 'USD',
//       error: null, 
//       rates: {}, 
//     }
//   },
//   created() {
//     this.fetchRates();
//   },
//   methods: {
//     async fetchRates() {
//       try {
//         const response = await axios.get(`https://openexchangerates.org/api/latest.json?app_id=${this.apiKey}`);
//         this.rates = response.data.rates;
//       } catch (error) {
//         this.error = "Ошибка при получении курсов валют.";
//       }
//     },
//   },
// }
</script>

<style scoped>

</style>
