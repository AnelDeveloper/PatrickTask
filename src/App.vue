<template>
  <div id="app">
    <nav class="navbar">

      <router-link to="/" class="navbar-brand"></router-link>
      <div class="navbar-nav mr-auto">
        <li class="nav-item">
          <router-link to="/tutorials" class="nav-link">Header</router-link>
        </li>

      </div>
    </nav>

    <div class="container mt-3">
      <router-view />
    </div>
    <CategoryPage />
    <ArtikalComp />



  </div>
</template>

<script>


import CategoryPage from './components/CategoryPage.vue'
import ArtikalComp from './components/ArtikalComp.vue';


export default {
  name: 'App',
  components: {
    CategoryPage,
    ArtikalComp
  },
  data() {
    return {
      Image: [

      ]
    }

  }




}





/// nav bar 

var prevScrollpos = window.pageYOffset;
window.onscroll = function () {
  var currentScrollPos = window.pageYOffset;
  if (prevScrollpos > currentScrollPos) {
    document.getElementById("navbar");
  } else {
    document.getElementById("navbar");
  }
  prevScrollpos = currentScrollPos;
}


</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.navbar {
  position: fixed;
  background-color: rgb(177, 177, 177);

  /* Black background color */

  /* Make it stick/fixed */
  top: 0;
  /* Stay on top */
  width: 100%;
  height: 60px;
  /* Full width */
  transition: top 0.3s;
  /* Transition effect when sliding down (and up) */

}

.nav-link {}
</style>


