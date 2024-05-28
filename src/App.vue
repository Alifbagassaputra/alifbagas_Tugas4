<template>
  <div id="app">
    <h1 class="title">Welcome to Our Restaurant</h1>
    <div class="container">
      <Menu @itemAdded="addToCart" />
      <Cart :items="cartItems" :totalPrice="cartTotalPrice" @removeItem="removeFromCart" />
    </div>
  </div>
</template>

<script>
import Menu from './components/Menu.vue';
import Cart from './components/Cart.vue';

export default {
  name: 'App',
  components: {
    Menu,
    Cart
  },
  data() {
    return {
      cartItems: JSON.parse(localStorage.getItem('cartItems')) || [],
      cartTotalPrice: 0
    };
  },
  created() {
    this.calculateTotalPrice();
  },
  methods: {
    addToCart(item) {
      this.cartItems.push(item);
      this.calculateTotalPrice();
      this.saveCart();
    },
    removeFromCart(index) {
      this.cartItems.splice(index, 1);
      this.calculateTotalPrice();
      this.saveCart();
    },
    calculateTotalPrice() {
      this.cartTotalPrice = this.cartItems.reduce((total, item) => total + item.price, 0);
    },
    saveCart() {
      localStorage.setItem('cartItems', JSON.stringify(this.cartItems));
    }
  }
};
</script>

<style>
#app {
  font-family: 'Arial', sans-serif;
  text-align: center;
  margin-top: 20px;
  background-color: #f0f4f8;
  padding: 20px;
}
.title {
  color: #42b983;
  font-size: 2.5em;
  margin-bottom: 20px;
}
.container {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  margin-top: 20px;
}
</style>
