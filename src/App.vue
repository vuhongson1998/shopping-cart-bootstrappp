<template>
  <nav id="nav" class="d-flex justify-content-center">
    <div class="menu-tab">
      <router-link id="nav_item_1" :class="{active: $route.name === 'Home'}" to="/">Home</router-link> ||
      <router-link id="nav_item_2" :class="{active: $route.name === 'Cart'}" to="/cart">Cart</router-link>
    </div>
  </nav>
  <router-view/>
</template>

<script>
export default {
  mounted() {
    this.$store.commit('updateCartFromLocalStorage')
  }
}
</script>
<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

html, body {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}

body {
  background-color: rgb(245, 245, 245);
}

#nav {
  padding: 10px;
  width: 100%;
  height: 53px;
  background-color: white;
  line-height: 30px;
  background-color: yellowgreen;
  position: fixed;
  z-index: 10000;

  a {
    font-weight: bold;
    color: #2c3e50;
    text-decoration: none;
    margin: 0 5px 0 5px;
    font-size: 1.25rem;
    
    &.router-link-active {
      color: teal;
    }
  }
}

.text-center {
  text-align: center;
}

.menu-tab {
  margin: 0px !important;
  padding: 0px;
  width: 150px !important;
  display: flex;

  a {
    float: left;
    width: 50%;
    cursor: pointer;

    &#nav_item_1 {
      text-align: end;
    }

    &#nav_item_2 {
      text-align: start;
    }

    &.router-link-active {
      border-bottom: 0.2rem solid #cc00ff;
    }
  }
}

</style>
