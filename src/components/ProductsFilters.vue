<template>
    <div>
        <div class="flex justify-between items-end">
            <h1 class="text-2xl">Products</h1>
            <input @keyup="search" v-model="searchTerm" type="text"
                   class="border h-12 w-1/2 border-gray-500 rounded-lg focus:outline-none px-3" placeholder="Search"/>
        </div>

        <div class="text-right mt-2">
            <input @keyup="maxPriceChanged" v-model="myMaxPrice" type="text"
                   class="border h-12 w-1/4 border-gray-500 rounded-lg focus:outline-none px-3"
                   placeholder="Maximum Price"/>
        </div>
    </div>
</template>

<script>
    export default {
        name: "ProductsFilters",

        data() {
            return {
                searchTerm: '',
                myMaxPrice: this.maxPriceProp
            }
        },

        computed: {
            maxPriceProp() {
                return this.maxPrice;
            }
        },

        props: {
            maxPrice: {}
        },

        methods: {
            search() {
                this.$emit('inputChanged', this.searchTerm)
            },

            maxPriceChanged() {
                this.$emit('maxPriceChanged', this.myMaxPrice)
            }
        },

    }
</script>

