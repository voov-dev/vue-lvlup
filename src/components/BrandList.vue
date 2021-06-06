<template>
  <div class="sort">
    <button class="btn -void -toggle start"
            :class="{ _show: isExpanded }"
            @click.prevent="toggleRiskLevels"
    >Filter by Brands</button>
    <div class="dropdown"
         :class="{ _show: isExpanded }"
    >
      <ul class="items">
        <li v-for="item in brandList"
            :key="item.id"
        >
          <label class="custom-checkbox"
                 :for="item.id">
            <input class="visually-hidden"
                   :id="item.id"
                   :value="item.code"
                   @change="$emit('brandSelected', selectedBrands)"
                   v-model="selectedBrands"
                   type="checkbox">
            <span class="text">{{ item.title }}</span>
          </label>
        </li>
      </ul>
      <button class="btn center"
              v-if="selectedBrands.length"
              @click.prevent="resetBrandList"
      >Clear all</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AppBrandtList',
  data: () => {
    return {
      selectedBrands: [],
      isExpanded: false
    }
  },
  props: {
    brandList: {
      type: Array,
      required: true
    }
  },
  methods: {
    resetBrandList() {
      this.selectedBrands = [];

      this.$emit('brandSelected', this.selectedBrands);
    },
    toggleRiskLevels() {
      this.isExpanded = !this.isExpanded;
    }
  }
}
</script>