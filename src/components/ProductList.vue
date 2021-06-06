<template>
  <ul class="product-grid"
      v-if="Array.isArray(productList) && productList.length"
  >
    <li v-for="item in productList"
        :key="item.id"
    >
      <AppSimpleProduct :simpleProduct="item"></AppSimpleProduct>
    </li>
  </ul>
  <div v-else>
    <h2>Try again</h2>
  </div>
</template>

<script>
import AppSimpleProduct from "./SimpleProduct";

export default {
  name: 'AppProductList',
  props: {
    productList: {
      type: Array,
      required: true
    },
  },
  components: { AppSimpleProduct }
}
</script>