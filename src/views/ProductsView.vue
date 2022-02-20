<template>
  <main class="wrapper">
    <h1>Products</h1>

    <div class="card-container">
      <ProductCardComponent v-for="(product, i) in inventory"
      :key="product.id"
      :index="i" :product="product" class="card"
      :addToCart="addToCart"/>
    </div>
  </main>
</template>

<script>
import ProductCardComponent from '@/components/ProductCardComponent.vue'

export default {

  props: {
    inventory: Object,
    addToCart: Function
  },
  components: {
    ProductCardComponent
  }
}
</script>
