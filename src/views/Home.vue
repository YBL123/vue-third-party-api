<template>
  <div class="home" v-if="products.length > 0">
  <div class="container">
    <ProductCard  v-for="product in products" :key="product.id" :id="product.id" :title="product.title" :image="product.image" :price="product.price" :description="product.description"/>
  </div>
  </div>
</template>

<script>
// @ is an alias to /src
import ProductCard from '@/components/Products.vue'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    ProductCard
  }, 
  data() {
    return {
      products: []
    }
  }, 
  async created() {
    try {
      const res = await axios.get('https://fakestoreapi.com/products')
      this.products = res.data
      console.log(this.products)
    } catch (err) {
      console.log(err)
    }
  }, 
  methods: {

  }
}
</script>
