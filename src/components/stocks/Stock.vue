<template>
<div id="my-stock" class="m-2">
  <div class="card bg-light">
    <div id="my-card-header" class="card-header">{{ stock.name }} <small>(Price: {{ stock.price }} )</small></div>
    <div class="card-body">
      <div class="d-flex justify-content-between align-items-center">
        <div class="mr-3">
          <input type="number"
          class="form-control"
          placeholder="Quantity"
          v-model.number="quantity"
          >
        </div>
        <div class="">
          <button
          class="btn btn-success"
          @click="buyStock"
          :disabled="quantity <= 0 || !Number.isInteger(quantity)"
           >
          Buy
          </button>
        </div>
      </div>

    </div>
  </div>

</div>
</template>

<script>
  export default {
    props: ['stock'],
    data() {
      return {
        quantity: 0
      }
    },
    methods: {
      buyStock() {
        const order = {
          stockId: this.stock.id,
          stockPrice: this.stock.price,
          quantity: this.quantity
        };
        console.log(order);
        this.quantity = 0
      }
    }
  };
</script>



<style scoped>
  #my-stock {
    min-width: 300px;
  }
  #my-card-header {
    background-color: rgba(138, 212, 157, .2);
  }
</style>
