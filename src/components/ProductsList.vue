<template>
    <div class="mt-5">
        <div v-for="(product, index) in products" :key="index" class="flex justify-between items-baseline mb-1">
            <h2>{{ product.name }}</h2>
            <div class="text-green-700 text-2xl">{{ product.price | priceFormat | euroSign }}</div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "ProductsList",

        filters: {
            priceFormat(value) {
                return `${value.toFixed(2)}`
            },

            euroSign(value) {
                return `€${value}`
            }
        },

        props: {
            products: {
                type: Array,
                required: true
            }
        }
    }
</script>

<style scoped>

</style>
