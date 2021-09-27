<template>
  <div id="products" class="">
    <product :premium="premium" @add-to-cart="updateCart" @remove-from-cart="removeCart"></product>
    <div class="cart">
      <p>Panier({{ cart.length }})</p>
    </div>
  </div>
</template>

<script>

import Product from '../components/Product.vue'

export default {
  components: {
    Product
  },

  data: function () {
    return {
      premium: true,
      cart: []
    }
  },
  methods: {
    updateCart (id) {
      this.cart.push(id)
    },
    removeCart (id) {
      for (var i = this.cart.length - 1; i >= 0; i--) {
        if (this.cart[i] === id) {
          this.cart.splice(i, 1)
        }
      }
    }
  }
}

</script>

<style scoped>

</style>
