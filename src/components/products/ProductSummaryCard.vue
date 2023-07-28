<template>
    <div class="col mb-4">
        <div class="card h-100">
            <img src="https://duhocthanhcong.vn/wp-content/uploads/school-photos/IMG%20Academy/IMG-Academy-Album1.jpg" class="card-img-top" alt="...">
            <div class="card-body">
                <h5 class="card-title">{{ product.name }}</h5>
                <h4 class="price">Price: ${{ product.price.toFixed(2) }}</h4>
                <p class="card-text">Description: {{ description }}</p>
                <p class="text-muted">{{ product.category }}</p>
                <button class="btn btn-sm view-product-button" @click="$emit('view-product', product)">View Product</button>
            </div>
        </div>
      </div>
</template>
<script>
    export default {
        props: ['product'],
        computed: {
            description() {
                return this.product.description.substring(0, 150)
            }
        }
    }
</script>
<style lang="scss" scoped>
    .card {
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        transition: 0.5s;
        border-radius: 5px;

        h5.price {
            color: gray;
        }

        p.description {
            font-size: .85rem;
        }

        p.text-muted {
            color: gray;
        }

        &:hover {
            box-shadow: 0 20px 40px 0 rgba(0,0,0,0.2);
        }
    }
</style>