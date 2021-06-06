<template>
  <article :id="simpleProduct.id"
           class="product">
    <div class="product-inner">
      <a class="image-wrap"
         href="#">
        <img class="image"
             :src="require(`@/assets${simpleProduct.image}`)"
             :alt="simpleProduct.title">
      </a>
      <div class="box">
        <div class="inner">
          <h3 class="title">
            <a href="#">{{ simpleProduct.title }}</a>
          </h3>
          <div class="price">
            <span class="currency">{{ simpleProduct.regular_price.currency }}</span>
            &nbsp;
            <span class="value">{{ simpleProduct.regular_price.value }}</span>
          </div>
        </div>
        <div class="dropdown">
          <button class="btn btn--buy"
                  @click.prevent="$root.$emit('addToCart', simpleProduct)"
          >Add to cart</button>
        </div>
      </div>
    </div>
  </article>
</template>

<script>
export default {
  name: 'AppSimpleProduct',
  props: {
    simpleProduct: {
      type: Object,
      required: true
    }
  }
}
</script>