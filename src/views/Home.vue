<template>
  <div id="app" >
    <aside class="aside">
      <div class="container">
        <div class="row">
          <AppBrandtList
              :brandList="brands"
              @brandSelected="chooseBrand"></AppBrandtList>
        </div>
      </div>
    </aside>
    <main class="content">
      <AppProductList :productList="filteredProductList"></AppProductList>
    </main>
  </div>
</template>

<script>
import AppProductList from "../components/ProductList";
import AppBrandtList from "../components/BrandList";

export default {
  components: {
    AppProductList,
    AppBrandtList
  },
  name: 'Home',
  data: () => {
    return {
      brands: [],
      products: [],
      selectedBrands: [],
    }
  },
  async mounted() {
    this.products = await require('../assets/products.json');
    this.brands = await require('../assets/brands.json');
  },
  computed: {
    filteredProductList() {
      if (!this.selectedBrands.length) {
        return this.products;
      }

      let selectedProducts = [];
      this.selectedBrands.forEach(brand => {
        selectedProducts.push(...this.products.filter(product => product.brand === brand.id));
      });

      return selectedProducts;
    }
  },
  methods: {
    chooseBrand(data) {
      this.selectedBrands = [];

      data.forEach(brandValue => {
        this.selectedBrands.push(...this.brands.filter(brand => brand.code === brandValue));
      });
    }
  },
}
</script>
