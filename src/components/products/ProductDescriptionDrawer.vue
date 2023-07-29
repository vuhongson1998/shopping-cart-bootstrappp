<template>
    <div class="sidenav" id="mySidenav">
        <a  class="closebtn" @click="$emit('close-product-drawer')">×</a>
        <div v-if="product" class="product-details">
            <h2>{{ product.name }}</h2>
            <div class="d-flex justify-content-center">
                <img src="https://duhocthanhcong.vn/wp-content/uploads/school-photos/IMG%20Academy/IMG-Academy-Album1.jpg" class="img-thumbnail rounded card-img-top" alt="...">
            </div>
            
            <p class="description">{{ product.description }}</p>
            <h3 class="text-center">${{ product.price.toFixed(2) }}</h3>
        
            <div v-show="product_total">
                <h5>Quantity In Cart: {{ product_total }}</h5>
            </div>

            <div class="button-container">
                <button class="remove view-product-button" @click="removeFromCart()">Remove</button>
                <button class="add view-product-button" @click="addToCart()">Add</button>
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
<style lang="scss" scoped>
.sidenav {
    height: 100%;
    width: 0;
    position: fixed;
    z-index: 1;
    top: 45px;
    left: 0;
    overflow-x: hidden;
    transition: 0.5s;
    padding-top: 60px;
    text-align:center;

    a {
        padding: 8px 8px 8px 32px;
        text-decoration: none;
        font-size: 25px;
        color: #818181;
        display: block;
        transition: 0.3s;
    }

    .closebtn {
        position: absolute;
        top: 0;
        right: 25px;
        font-size: 36px;
        margin-left: 50px;
        cursor: pointer;
    
        &:hover {
            color: black;
        }
    }
}
  
.product-details {
    background-color: white;
    display: flex;
    justify-content: center;
    flex-direction: column;

    p.description {
        padding: 20px;
        line-height: 1.5rem;
    }

    .button-container {
        button {
            font-size: 15px;
            width: 80px;
            margin: 0 5px 50px 5px;
        }
    }
}
  
@media (min-width: 1000px) {
    .product-details .card-img-top {
        width: 60% !important;
    }
}

  
</style>