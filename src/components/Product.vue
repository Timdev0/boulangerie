<template>
  <div id="product-component">
    <div class="container">
      <div class="row">
        <div class="product-img col-sm-6">
          <img class="img-fluid" v-bind:src="image" alt="">
        </div>
        <div class="product-info col-sm-6">
          <h1>{{ title }}</h1>
          <p>{{ description }} <a :href="link" target="_blank">Produits semblables</a></p>
          <p v-if="inStock > 5">En Stock</p>
          <p v-else-if="inStock <= 5 && inStock > 0">Presque épuisé</p>
          <p v-else
            :class="{ lineThrought: inStock <= 0 }">
            Artcile épuisé
          </p>
          <p v-if="onSale">{{ onSaleTxt }}est en promo !</p>
          <p>{{ offer }}</p>
          <product-details :details="details"></product-details>
          <div v-for="(variant, index) in variants"
              :key="variant.variantId"
              class="color-box"
              :style="{ backgroundColor: variant.variantColor }"
              @mouseover="updateProduct(index)">
              <span>{{ variant.variantType }}</span>
          </div>
          <button v-on:click="addToCart" class="btn btn-primary" :disabled="inStock<=0">Ajouté au panier</button>
          <button @click="removeFromCart" class="btn btn-danger">-</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ProductDetails from './ProductDetails.vue'

export default {
  components: {
    ProductDetails
  },

  props: {
    premium: {
      type: Boolean,
      requiered: true
    }
  },

  data: function () {
    return {
      category: 'Pain',
      product: 'Baguette',
      description: 'Les baguettes sont préparées le matin même.',
      link: 'https://www.amazon.fr/s?k=baguette+de+pain&__mk_fr_FR=%C3%85M%C3%85%C5%BD%C3%95%C3%91&ref=nb_sb_noss_2',
      onSale: true,
      selectVariant: 0,
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
          variantColor: '#f8c291',
          variantQuantity: 4
        },
        {
          variantId: 1001,
          variantType: 'Aux céréales',
          variantImage: require('../assets/baguette-cereales.jpeg'),
          variantColor: '#e58e26',
          variantQuantity: 0
        }
      ]
    }
  },

  methods: {
    addToCart: function () {
      this.$emit('add-to-cart', this.variants[this.selectVariant].variantId)
    },
    updateProduct (index) {
      this.selectVariant = index
      console.log(index)
    },
    removeFromCart: function () {
      this.$emit('remove-from-cart', this.variants[this.selectVariant].variantId)
    }
  },

  computed: {
    title () {
      return this.category + ' | ' + this.product
    },
    onSaleTxt () {
      return 'Le ' + this.category + ' : ' + this.product + ' '
    },
    image () {
      return this.variants[this.selectVariant].variantImage
    },
    inStock () {
      return this.variants[this.selectVariant].variantQuantity
    },
    offer () {
      if (this.premium) {
        return '2 achetés 3ème offerte'
      }
      return ''
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

    .lineThrought{
      text-decoration: line-through;
    }
</style>
