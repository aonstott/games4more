<template>
<div>
  <div class="pure-menu pure-menu-horizontal">
    <ul class="pure-menu-list">
      <li class="pure-menu-item"><a @click="select('Console')" href="#" class="pure-menu-link">Console</a></li>
      <li class="pure-menu-item"><a @click="select('Game')" href="#" class="pure-menu-link">Game</a></li>
      <li class="pure-menu-item"><a @click="select('Controller')" href="#" class="pure-menu-link">Controller</a></li>
      <li class="pure-menu-item"><a @click="select('Other')" href="#" class="pure-menu-link">Other</a></li>
    </ul>
  </div>
  <ProductList :products="products" />
</div>
</template>



<script>
import ProductList from "../components/ProductList.vue"
export default {
  name: 'Browse',
  components: {
    ProductList
  },
  data() {
    return {
      country: '',
    }
  },
  computed: {
    products() {
      return this.$root.$data.products.filter(product => product.country === this.country);
    }
  },
  methods: {
    select(country) {
      this.country = country;
    }
  }
}
</script>
