<template>
  <div id="product container">
    <div class="row">
      <div class="product-img col-sm-6">
        <img class="img-fluid" v-bind:src="image" alt="">
      </div>
      <div class="product-info col-sm-6">
        <h1>{{ product }}</h1>
        <p v-if="inStock > 5">En Stock</p>
        <p v-else-if="inStock <= 5 && inStock > 0">Presque épuisé</p>
        <p v-else>Artcile épuisé</p>
        <ul>
          <li v-for="detail in details" :key=detail.detailId>{{ detail.detailText }}</li>
        </ul>
        <div v-for="variant in variants" :key="variant.variantId">
          <p @mouseover="updateProduct(variant.variantImage)">{{ variant.variantType }}</p>
        </div>
        <button v-on:click="addToCart" class="btn btn-primary">Ajouté au panier</button>
        <button @click="removeToCart" class="btn btn-danger">-</button>
        <div class="cart">
          <p>Panier({{ cart }})</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      product: 'Baguette',
      image: require('../assets/baguette.jpeg'),
      inStock: 0,
      cart: 0,
      details: [
        {
          detailId: 10,
          detailText: 'Farine de blé Label Rouge'
        },
        {
          detailId: 11,
          detailText: 'Allergène : Gluten'
        }
      ],
      variants: [
        {
          variantId: 1000,
          variantType: 'Nature',
          variantImage: require('../assets/baguette.jpeg')
        },
        {
          variantId: 1001,
          variantType: 'Aux céréales',
          variantImage: require('../assets/baguette-cereales.jpeg')
        }
      ]
    }
  },
  methods: {
    addToCart: function () {
      this.cart += 1
    },
    removeToCart: function () {
      this.cart -= 1
    },
    updateProduct (variantImage) {
      this.image = variantImage
    }
  }
}
</script>
