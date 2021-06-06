<template>
  <div class="cart">
    <svg class="icon" width="22" height="20" viewBox="0 0 22 20" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M1 1h3.636l2.437 11.477c.083.395.31.75.643 1.002a1.89 1.89 0 001.175.378h8.836c.427.008.843-.126 1.175-.378a1.7 1.7 0 00.643-1.002L21 5.286H5.545m3.637 12.857c0 .473-.407.857-.91.857-.501 0-.908-.384-.908-.857 0-.474.407-.857.909-.857s.909.383.909.857zm10 0c0 .473-.407.857-.91.857-.501 0-.908-.384-.908-.857 0-.474.407-.857.909-.857s.909.383.909.857z" stroke="currentColor " stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>
    <span class="count">{{ cartCounter }}</span>
  </div>
</template>

<script>
export default {
  name: 'AppCart',
  data: () => {
    return {
      items: [],
      cartCounter: 0
    }
  },
  created() {
    this.updateCartCounter();
  },
  mounted() {
    this.$root.$on('addToCart', (data) => {
      this.addToCart(data);
      this.updateCartCounter();
    });
  },
  methods: {
    addToCart(product) {
      if (window?.localStorage) {
        const cart = JSON.parse(localStorage.getItem('cart')) || [];
        const candidateId = cart.findIndex((item) => {
          return item.id === product.id;
        });

        if (~candidateId) {
          cart[candidateId].qty = ++cart[candidateId].qty;
        } else {
          cart.push(
              Object.assign({}, product, { qty: 1 })
          );
        }

        localStorage.setItem('cart', JSON.stringify(cart));
      }
    },
    updateCartCounter() {
      const cartProducts = JSON.parse(localStorage.getItem('cart'));

      if (cartProducts?.length) {
        this.items = cartProducts;
        this.cartCounter = 0;
        cartProducts.forEach((item) => {
          this.cartCounter += Number(item.qty);
        });
      }
    }
  },
}
</script>
