<template>
    <div id="product-details-component">
      <ul>
        <li v-for="detail in details" :key="detail.detailId">{{ detail.detailText }}</li>
      </ul>
    </div>
</template>

<script>
export default {
  props: {
    details: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>

</style>
