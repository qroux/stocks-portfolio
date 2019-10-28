<template>
<div id="my-stock" class="m-2">
  <div class="card bg-light">
    <div id="my-card-header" class="card-header">{{ stock.name }} <small>(Price: {{ stock.price }} )</small></div>
    <div class="card-body">
      <div>
        <h6 v-if="insufficientFunds">Insufficient Funds</h6>
        <h6 v-else-if="quantity == 0"> - </h6>
        <h6 v-else>
          Total: {{ quantity }} x {{ stock.price }} = {{ total() }}
        </h6>
      </div>
      <div class="d-flex justify-content-between align-items-center">
        <div class="mr-3">
          <input type="number"
          min="0"
          class="form-control"
          placeholder="Quantity"
          v-model.number="quantity"
          :class="{danger: insufficientFunds}"

          >
        </div>
        <div class="">
          <button
          class="btn btn-success"
          @click="buyStock"
          :disabled="insufficientFunds || quantity <= 0 || !Number.isInteger(quantity)"
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
        this.$store.dispatch('buyStock', order);
        this.quantity = 0;
      },
      total() {
        return this.quantity * this.stock.price
      }
    },
    computed: {
      insufficientFunds() {
        return (this.quantity * this.stock.price) > this.$store.getters.funds
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
  .danger {
    border-color: rgba(189,0,0, .5);
    box-shadow: 0px 1px 1px rgba(189, 0, 0, 0.075) inset, 0px 0px 8px rgba(189, 0, 0, 0.5);
  }
</style>
