<template>
  <div class="mt-5">
    <h1>List of Stocks</h1>
    <div class="d-flex flex-wrap justify-content-between">
      <app-stock v-for="stock in stocks" :stock="stock" ></app-stock>
    </div>
  </div>
</template>

<script>
  import Stock from './Stock.vue'


  export default {
    data() {
      return {
        stocks: [
          { id: 1, name: 'BMW', price: 100 },
          { id: 2, name: 'GM', price: 150 },
          { id: 3, name: 'FORD', price: 200 }
        ]
      }
    },
    components: {
      appStock: Stock
    }
  }
</script>

<style scoped>

</style>
