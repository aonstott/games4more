<template>
<div class="dumdum">
  <div class="wrapper">
    <div class="products">
      <div v-if="this.$root.$data.cart.length == 0">
        Cart is empty!
      </div>
      <div v-else class="product" v-for="item in this.$root.$data.cart" :key="item.id2">
        <div class="info">
          <h1>{{item.name}}</h1>
          <p>{{item.country}}</p>
        </div>
        <div class="image">
          <img :src="'/images/products/'+item.image">
        </div>
        <div class="price">
          <h2>{{item.price}}</h2>
          <button @click="remove(item)" class="auto">Remove</button>
        </div>
      </div>
    </div>
  </div>
  <div class="pp">
    <p class="totalPrice">Total Price: $ {{total}} </p>
  </div>
</div>
</template>


<script>
export default {
  name: 'Cart',
  props: {
    cart: Array
  },
  methods: {
    remove(product) {
      this.$root.$data.cart.splice(this.$root.$data.cart.indexOf(product), 1);
      console.log(this.$root.$data.cart)
    }
  },
  computed: {
    total() {
      let sum = 0;
      let arr = [];
      arr = this.$root.$data.cart;
      for (let i = 0; i < this.$root.$data.cart.length; i++) {
        sum += parseFloat(arr[i].price.substring(1));
        console.log(arr[i].price.substring(1));
      }
      console.log(sum);
      return sum.toFixed(2);
    }
  }
}
</script>

<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.products {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.product {
  margin: 10px;
  margin-top: 50px;
  width: 200px;
}

.product img {
  border: 2px solid #333;
  height: 250px;
  width: 200px;
  object-fit: cover;
}

.product .image {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.info {
  background: #56F;
  color: #000;
  padding: 10px 30px;
  height: 80px;
}

.info h1 {
  font-size: 16px;
}

.info h2 {
  font-size: 14px;
}

.info p {
  margin: 0px;
  font-size: 10px;
}


.price {
  display: flex;
}

button {
  height: 50px;
  background: #000;
  color: white;
  border: none;
}

.auto {
  margin-left: auto;
}

.totalPrice {
  text-align: center;
  margin-top: 50px;
  font-size: 30px;
}
</style>
