<template>
  <div id="product-review-component">
    <form class="review-form" @submit.prevent="onSubmit">
      <p v-if="errors.length">
        <ul>
          <li v-for="error in errors" :key="error.errorId">{{ error }}</li>
        </ul>
      </p>
      <div class="form-group">
        <label for="name">Nom :</label>
        <input class="form-control" id="name" v-model="name">
      </div>

      <div class="form-group">
        <label for="review">Avis :</label>
        <textarea class="form-control" id="review" v-model="review"></textarea>
      </div>
      <div class="form-group">
        <label for="rating">Note :</label>
        <select class="form-control" name="rating" id="rating" v-model.number="rating">
          <option value="1">1</option>
          <option value="2">2</option>
          <option value="3">3</option>
          <option value="4">4</option>
          <option value="5">5</option>
        </select>
      </div>

      <button class="btn btn-primary" type="submit">Envoyer</button>
    </form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      name: null,
      review: null,
      rating: null,
      errors: []
    }
  },
  methods: {
    onSubmit () {
      if (this.name && this.review && this.rating) {
        const productReview = {
          name: this.name,
          review: this.review,
          rating: this.rating
        }
        this.$emit('review-submitted', productReview)
        this.name = null
        this.review = null
        this.rating = null
      } else {
        if (!this.name) this.errors.push('Nom requis.')
        if (!this.review) this.errors.push('Avis requis.')
        if (!this.rating) this.errors.push('Note requise.')
      }
    }
  }
}
</script>
