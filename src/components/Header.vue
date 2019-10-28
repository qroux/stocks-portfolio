<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light px-4">
    <router-link to='/' activeClass="active navbar-brand"><a>Stock Trader</a></router-link>
    <button class="navbar-toggler" type="button">
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav mr-auto">
        <router-link tag="li" to='/portfolio' activeClass="active"><a class="nav-link">Portfolio</a></router-link>
        <router-link tag="li" to='/stocks' activeClass="active"><a class="nav-link">Stocks</a></router-link>
      </ul>
      <ul class="navbar-nav">
        <li class="nav-item mr-2">
          <a class="nav-link" href="#">End Day</a>
        </li>
        <li class="nav-item dropdown mr-2">
          <a
            class="nav-link dropdown-toggle"
            href="#" id="navbarDropdown"
            role="button"
            data-toggle="dropdown"
            aria-haspopup="true"
            aria-expanded="false">
            Save & Load
          </a>
          <div class="dropdown-menu" aria-labelledby="navbarDropdown">
            <li><a class="dropdown-item" href="#">Save Data</a></li>
            <li><a class="dropdown-item" href="#">Load Data</a></li>
            <div class="dropdown-divider"></div>
            <li><a class="dropdown-item" href="#">Something else here</a></li>
          </div>
        </li>
        <li class="navbar-text"><strong>( Funds: {{ funds }} ) </strong></li>
      </ul>
    </div>
  </nav>
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

<style scoped>
  .active {
    font-color: black;
  }
  .navbar {
    border: 1px solid rgba(201, 201, 201, .3);
  }
</style>
