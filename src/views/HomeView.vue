<template>
  <div class="splash-container">
    <div class="splash">
      <h1>Splendid Food</h1>
    </div>
  </div>

  <main class="wrapper">
    <h2>Recommended</h2>

    <div class="recommended">
      <ProductCardComponent v-for="(product, i) in inventory.slice(0, 3)"
      :key="product.id"
      :index="i" :product="product" class="card"
      :addToCart="addToCart"/>
    </div>
  </main>
</template>

<script>
import ProductCardComponent from '@/components/ProductCardComponent.vue'

export default {
  name: 'HomeView',
  props: {
    inventory: Object,
    addToCart: Function
  },
  components: {
    ProductCardComponent
  }
}
</script>
