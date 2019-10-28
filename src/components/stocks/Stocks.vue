<template>
  <div class="container mt-5">
    <h1>List of Stocks</h1>
    <div class="d-flex flex-wrap justify-content-between">
      <app-stock v-for="stock in stocks" :stock="stock" ></app-stock>
    </div>
  </div>
</template>

<script>
  import Stock from './Stock.vue'

  export default {
    components: {
      appStock: Stock
    },
    computed: {
      stocks() {
        return this.$store.getters.stocks;
      }
    }
  }
</script>

<style scoped>
</style>
