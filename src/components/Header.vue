<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
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
        <li class="nav-item">
          <a class="nav-link" href="#">End Day</a>
        </li>
        <li class="nav-item dropdown">
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
      </ul>
    </div>
  </nav>
</template>

<script>
</script>

<style scoped>
  .active {
    font-color: black;
  }
</style>
