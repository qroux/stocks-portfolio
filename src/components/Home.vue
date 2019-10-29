<template>
  <div class="container mt-5">
    <h1>Trade or view your Portfolio</h1>
    <h6>1) You may Save & Load your Data</h6>
    <h6>2) Click on 'End Day' to begin a new Day!</h6>
    <hr>
    <p>Your Funds: {{ funds | currency }} </p>
  </div>
</template>



<script>
  export default {
    computed: {
      funds() {
        return this.$store.getters.funds
      }
    }
  }
</script>
