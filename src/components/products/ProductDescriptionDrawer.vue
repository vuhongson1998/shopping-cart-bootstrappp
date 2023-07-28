<template>
    <div class="sidenav" id="mySidenav">
        <a  class="closebtn" @click="$emit('close-product-drawer')">×</a>
        <div v-if="product" class="product-details">
            <h2>{{ product.name }}</h2>
            <div class="d-flex justify-content-center">
                <img src="https://duhocthanhcong.vn/wp-content/uploads/school-photos/IMG%20Academy/IMG-Academy-Album1.jpg" class="card-img-top" alt="...">
            </div>
            
            <p class="description">{{ product.description }}</p>
            <h3 class="text-center">${{ product.price.toFixed(2) }}</h3>
        
            <div class="cart-total" v-if="product_total">
                <h3>In Cart</h3>
                <h4>{{ product_total }}</h4> 
            </div>

            <div class="button-container">
                <button class="remove" @click="removeFromCart()">Remove</button>
                <button class="add" @click="addToCart()">Add</button>
            </div>
        </div>
    </div>
    
</template>
<script>
export default {
    props: ['product'],
    methods: {
        addToCart() {
            this.$store.commit('addToCart', this.product)
        },
        removeFromCart() {
            this.$store.commit('removeFromCart', this.product)
        }
    },
    computed: {
        product_total() {
            return this.$store.getters.productQuantity(this.product)
        }
    }
}
</script>
<style lang="scss">
.sidenav {
    height: 100%;
    width: 0;
    position: fixed;
    z-index: 1;
    top: 0;
    left: 0;
    background-color: white;
    overflow-x: hidden;
    transition: 0.5s;
    padding-top: 60px;
    padding-right: 0px;
    text-align:center;
  }
  
  .sidenav a {
    padding: 8px 8px 8px 32px;
    text-decoration: none;
    font-size: 25px;
    color: #818181;
    display: block;
    transition: 0.3s;
  
  }
  
  .sidenav a:hover{
    color: #f1f1f1;
  }
  
  .sidenav .closebtn {
    position: absolute;
    top: 0;
    right: 25px;
    font-size: 36px;
    margin-left: 50px;
  }

  .product-details {
    display: flex;
    justify-content: center;
    flex-direction: column;

    p.description {
        padding: 20px;
        line-height: 1.5rem;
    }

    .button-container {
        button {
            width: 150px;
            border: none;
            padding: 10px;
            border-radius: 5px;
            margin: 0 5px 50px 5px;
            cursor: pointer;

        }
    }
}
  

  
  @media (min-width: 1000px) {
    .product-details .card-img-top {
        width: 70% !important;
    }
  }

  
</style>