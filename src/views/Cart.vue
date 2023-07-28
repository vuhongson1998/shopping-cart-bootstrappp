<template>
    <div>
        <h1>Your Cart</h1>
        <div class="cart-item-card">
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