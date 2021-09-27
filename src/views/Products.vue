<template>
  <div id="products" class="">
    <product :premium="premium" @add-to-cart="updateCart" @remove-from-cart="removeCart"></product>
    <div class="cart">
      <p>Panier({{ cart.length }})</p>
    </div>
    <div>
      <h2>Avis</h2>
      <p>Aucun avis pour le moment</p>
      <ul>
        <li v-for="review in reviews" :key="review.reviewID">
          <p>{{ review.name }}</p>
          <p>{{ review.rating }}</p>
          <p>{{ review.review }}</p>
        </li>
      </ul>
    </div>
    <product-review @review-submitted="addReview"></product-review>
  </div>
</template>

<script>

import Product from '../components/Product.vue'
import ProductReview from '../components/ProductReview.vue'

export default {
  components: {
    Product,
    ProductReview
  },

  data: function () {
    return {
      premium: true,
      cart: [],
      reviews: []
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
    },
    addReview (productReview) {
      this.reviews.push(productReview)
    }
  }
}

</script>

<style scoped>

</style>
