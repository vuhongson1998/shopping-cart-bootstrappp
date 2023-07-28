<template>
  <div class="home">
    <h1>Featured Products</h1>
    <div class="row row-cols-1 row-cols-md-4 p-4">
      <ProductDescriptionDrawer 
        :product="product"
        v-on:close-product-drawer="closeNav()"
      />
      <ProductSummaryCard 
        v-for="product in items"
        :key="product.id"
        :product="product"
        v-on:view-product="viewProduct($event)"
      />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import items from '../data/items.js'
import ProductDescriptionDrawer from '../components/products/ProductDescriptionDrawer.vue'
import ProductSummaryCard from '@/components/products/ProductSummaryCard.vue'

export default {
  name: 'HomeView',
  components: {
    ProductSummaryCard,
    ProductDescriptionDrawer
  },
  data() {
    return {
      items: items,
      product: null
    }
  },
  mounted() {
    this.closeNav()
  },
  methods: {
    viewProduct(product) {
      this.openNav()
      this.product = product
    },
    openNav() {
      document.getElementById("mySidenav").style.backgroundColor = "#fff"
      document.getElementById("mySidenav").style.width = "100%";
    },
    closeNav() {
      this.product = null
      document.getElementById("mySidenav").style.backgroundColor = "unset"
      document.getElementById("mySidenav").style.width = "0";
    }
  }
}
</script>
<style lang="scss">
@media (min-width: 576px) { 
  .home {
      position: absolute;
      width: 80%;
      left: 0;
      right: 0;
      margin: 0 auto;
  }
}
</style>