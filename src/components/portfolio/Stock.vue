<template>
<div id="my-stock" class="m-2">
  <div class="card bg-light">
    <div id="my-card-header" class="card-header">{{ stock.name }} <small>(Price: {{ stock.price }} | quantity: {{ stock.quantity }} )</small></div>
    <div class="card-body">
      <div class="d-flex justify-content-between align-items-center">
        <div class="mr-3">
          <input type="number"
          min="0"
          :max="maxLimit()"
          class="form-control"
          placeholder="Quantity"
          v-model.number="quantity"
          :class="{danger: insufficientQuantity}"
          >
        </div>
        <div class="">
          <button
          class="btn btn-success"
          @click="sellStock"
          :disabled=" insufficientQuantity || quantity <= 0 || !Number.isInteger(quantity)"
           >
          Sell
          </button>
        </div>
      </div>

    </div>
  </div>

</div>
</template>

<script>
  import {mapActions} from 'vuex'

  export default {
    props: ['stock'],
    data() {
      return {
        quantity: 0
      }
    },
    methods: {
      ...mapActions({
          placeSellOrder: 'sellStock'
        }),
      sellStock() {
        const order = {
          stockId: this.stock.id,
          stockPrice: this.stock.price,
          quantity: this.quantity
        };
        this.placeSellOrder(order);
        this.quantity = 0;
      },
      maxLimit() {
        return this.stock.quantity
      }
    },
    computed: {
      insufficientQuantity() {
        return this.quantity > this.stock.quantity
      }
    }
  };
</script>



<style scoped>
  #my-stock {
    min-width: 300px;
  }
  #my-card-header {
    background-color: rgba(92, 198, 255, .2);
  }
  .danger {
    border-color: rgba(189,0,0, .5);
    box-shadow: 0px 1px 1px rgba(189, 0, 0, 0.075) inset, 0px 0px 8px rgba(189, 0, 0, 0.5);
  }
</style>
