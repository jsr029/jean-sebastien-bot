<template>
  <nav class="navbar navbar-dark bg-primary" role="navigation">
    <a class="navbar-brand" href="#">Jsr029</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav"
      aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon" @click='active = !active'></span>
    </button>
    <div class="navbar-collapse" :class="{ 'collapse': active }" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item active">
          <router-link to="/" class="nav-link"><span class="sr-only">Home</span></router-link>
        </li>
        <li class="nav-item">
          <router-link to="/about" class="nav-link"><span class="sr-only">About</span></router-link>
        </li>
      </ul>
    </div>
  </nav>
  <router-view />
</template>
<script>
export default {
  name: 'App',
  components: {},
  data: function () {
    return {
      active: true
    }
  }
}
</script>
<style>
nav {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
}

.navbar-brand {
  margin-left: 5px;
}

.navbar-toggler {
  margin-right: 5px;
}
</style>
