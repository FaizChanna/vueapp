<template>
  <nav class="navbar navbar-expand-lg navbar-dark mb-4" id="nav">
    <div class="container">
      <router-link class="nav-link" to="/"> {{SiteTitle}}</router-link>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ml-auto">
          <li class="nav-item active">
            <router-link class="nav-link" to="/">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/about">About</router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'Header',
  data(){
    return{
      SiteTitle: "Vue Basic App"
    }
  }
}
</script>
<style scoped>
.navbar {
  background: #1a1d24;
}
.navbar-nav a {
  color: #fff;
  padding: 0 15px;
  display: block;
}
.nav-link{
  color:#fff;
  font-size: 18px;
}
</style>