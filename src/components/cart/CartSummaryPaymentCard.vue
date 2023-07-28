<template>
        <tr>
            <th colspan="3" class="cart-total">Cart Total</th>
            <td class="text-center">${{ cart_total.toFixed(2) }}</td>
        </tr>
        <tr>
            <th colspan="3" class="cart-total"></th>
            <td class="text-center"><button class="view-product-button m-2 ">Pay by Credit Card</button></td>
        </tr>
      
        
</template>
<script>
    export default {
        computed: {
            cart_total() {
                return this.$store.getters.cartTotal
            }
        }
    }
</script>
<style lang="scss" scoped>
@media (min-width: 1200px) {
    .cart-total {
        padding-left: 40px !important;
    }
}
</style>