<template>
  <div id="app">
      <!-- navbar -->
      <div class="container">
        <b-navbar>
          <template slot="brand">
            <b-navbar-item tag="router-link" to="/" >Home</b-navbar-item>
          </template>
          <template slot="start">
              <b-navbar-item tag="router-link" to="/blog">Blog</b-navbar-item>
              <b-navbar-item tag="router-link" to="/services">Services</b-navbar-item>
              <b-navbar-item tag="router-link" to="/contact">contact</b-navbar-item>
          </template>
        </b-navbar>
      </div>
      <div class="container">
       <transition name="moveInUp">
         <router-view/>
       </transition>
        
      </div>
    
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.moveInUp-enter-active{
  animation: fadeIn 2s ease-in;
}
@keyframes fadeIn{
  0%{
    opacity: 0;
  }
  50%{
    opacity: 0.5;
  }
  100%{
    opacity: 1;
  }
}

.moveInUp-leave-active{
  animation: moveInUp .3s ease-in;
}
@keyframes moveInUp{
 0%{
  transform: translateY(0);
 }
  100%{
  transform: translateY(-400px);
 }
}
</style>
