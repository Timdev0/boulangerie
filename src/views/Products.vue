<template>
  <div id="products" class="container">
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
          <li v-for="detail in details" :key="detail.detailId">{{ detail.detailText }}</li>
        </ul>
        <div v-for="variant in variants"
            :key="variant.variantId"
            class="color-box"
            :style="{ backgroundColor: variant.variantColor }"
            @mouseover="updateProduct(variant.variantImage)">
            <span>{{ variant.variantType }}</span>
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
          variantImage: require('../assets/baguette.jpeg'),
          variantColor: '#f8c291'
        },
        {
          variantId: 1001,
          variantType: 'Aux céréales',
          variantImage: require('../assets/baguette-cereales.jpeg'),
          variantColor: '#e58e26'
        }
      ]
    }
  },
  methods: {
    addToCart: function () {
      this.cart += 1
    },
    removeToCart: function () {
      if (this.cart > 0) {
        this.cart -= 1
      }
    },
    updateProduct (variantImage) {
      this.image = variantImage
    }
  }
}
</script>

<style scoped>
.color-box{
  width: 10rem;
  height: 2.5rem;
  margin-top: 0.5rem;
  margin-bottom: 0.5rem;
  display: inline-block;
  text-align: center;
  text-decoration: none;
  vertical-align: middle;
  border: 1px solid transparent;
  padding: .375rem .75rem;
  font-size: 1rem;
  border-radius: .25rem;
  line-height: 1.5;
  }
</style>
