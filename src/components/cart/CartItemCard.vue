<template>
    <tr>
        <th scope="row" class="text-center">{{ index + 1 }}</th>
        <td class="text-center">{{ product.name }}</td>
        <td class="text-center">{{ product.quantity }}</td>
        <td class="text-center">${{ item_cost.toFixed(2) }}</td>
    </tr>
</template>

<script>
export default {
    props: ['product', 'index'],
    computed: {
        description() {
            return this.product.description.substring(0, 120)
        },
        item_cost() {
            return this.product.price * this.product.quantity
        }
    }
}
</script>
