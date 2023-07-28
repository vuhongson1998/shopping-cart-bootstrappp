<template>
    <div>
        <h1 class="pt-2 pb-3">Your Cart</h1>
        <div class="cart-item-card" v-show="products.length">
            <table class="table">
                <thead>
                <tr>
                    <th scope="col" class="text-center">No</th>
                    <th scope="col" class="text-center">Product Name</th>
                    <th scope="col" class="text-center">Quantity</th>
                    <th scope="col" class="text-center">Total Cost</th>
                </tr>
                </thead>
                <tbody>
                    <CartItemCard 
                    v-for="(product, index) in products" 
                    :key="product.id"
                    :index="index"
                    :product="product"
                    />

                    <CartSummaryPaymentCard />
                </tbody>
            </table>
        </div>
        <h3 v-show="!products.length">No products in the cart!</h3>
    </div>
</template>
<script>
import CartItemCard from '../components/cart/CartItemCard.vue'
import CartSummaryPaymentCard from '../components/cart/CartSummaryPaymentCard.vue'
export default {
    name: "CartPage",
    components: {
        CartItemCard,
        CartSummaryPaymentCard
    },
    computed: {
        products() {
            return this.$store.getters.cartItems
        }
    }
}
</script>
<style lang="scss" scoped>
.cart-item-card {
    width: 90%;
    margin: 0 auto;
    background-color: white;
    box-shadow: 0 0 5px gray;
    border-radius: 5px;
    text-align: left;

    .header {
        display: flex;
        justify-content: space-around;
    }
}
</style>