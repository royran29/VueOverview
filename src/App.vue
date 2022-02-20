<template>
  <header class="top-bar spread">
    <nav class="top-bar-nav">
      <router-link to="/" class="top-bar-link">
        <i class="icofont-spoon-and-fork"></i>
        <span>Home</span>
      </router-link>
      <router-link to="/products" class="top-bar-link">
        <span>Products</span>
      </router-link>
    </nav>
    <div @click="toggleSidebar" class="top-bar-cart-link">
      <i class="icofont-cart-alt icofont-1x"></i>
      <span>Cart ({{ totalQuantity }})</span>
    </div>
  </header>

  <router-view :inventory="inventory" :addToCart="addToCart"/>

  <SidebarComponent v-if="showsidebar"
    :toggle="toggleSidebar"
    :cart="cart"
    :inventory="inventory"
    :remove="removeItemFromCart"
  />
</template>

<script>
import SidebarComponent from '@/components/SidebarComponent.vue'
import food from './food.json'

export default {

  components: {
    SidebarComponent
  },

  data () {
    return {
      showsidebar: false,
      inventory: food,
      cart: {}
    }
  },

  methods: {
    addToCart (name, quantity) {
      if (!this.cart[name]) this.cart[name] = 0
      this.cart[name] += quantity
    },
    toggleSidebar () {
      this.showsidebar = !this.showsidebar
    },
    removeItemFromCart (name) {
      delete this.cart[name]
    }
  },

  computed: {
    totalQuantity () {
      return Object.values(this.cart).reduce((acc, curr) => acc + curr, 0)
    }
  }
}
</script>
