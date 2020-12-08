<template>
    <div class="container max-w-5xl m-auto mt-16">
        <ProductsFilters @inputChanged="search" @maxPriceChanged="maxPriceChanged" :maxPrice="maxPrice"/>

        <ProductsList :products="filteredProducts"/>
    </div>
</template>

<script>
    import ProductsList from "./ProductsList"
    import ProductsFilters from "./ProductsFilters";

    export default {
        name: "ProductsComponent",

        data() {
            return {
                products: [
                    {
                        name: 'Φάκες Belunga',
                        price: 4
                    },
                    {
                        name: 'Ταχίνι Όλυμπος',
                        price: 5.6
                    },
                    {
                        name: 'Nescafe Cappuccino',
                        price: 3.87
                    },
                    {
                        name: "Kellogg's",
                        price: 2.77
                    },
                    {
                        name: 'Misko No6',
                        price: 1.23
                    }
                ],
                filteredProducts: [],
            }
        },

        computed: {
            maxPrice() {
                let max = 0;

                this.filteredProducts.forEach(product => {
                    if (product.price > max) {
                        max = product.price
                    }
                })

                return max;
            }
        },

        methods: {
            search(term) {
                this.filteredProducts = this.products.filter(product => {
                    return product.name.toLowerCase().includes(term.toLowerCase())
                })
            },

            maxPriceChanged(value) {
                this.filteredProducts = this.filteredProducts.filter(product => {
                    return product.price <= value
                })
            }
        },

        mounted() {
            this.filteredProducts = this.products
        },

        components: {
            ProductsList,
            ProductsFilters
        }
    }
</script>

