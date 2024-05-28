<template>
  <div class="cart">
    <h2>Cart</h2>
    <ul class="cart-list">
      <li v-for="(item, index) in items" :key="index" class="cart-item card">
        <span class="item-name">{{ item.name }}</span>
        <span class="item-price">${{ item.price }}</span>
        <button @click="removeItem(index)" class="remove-button">Remove</button>
      </li>
    </ul>
    <p class="total-price">Total Price: ${{ totalPrice }}</p>
  </div>
</template>

<script>
export default {
  props: {
    items: {
      type: Array,
      required: true
    },
    totalPrice: {
      type: Number,
      required: true
    }
  },
  methods: {
    removeItem(index) {
      this.$emit('removeItem', index);
    }
  }
};
</script>

<style scoped>
.cart {
  width: 45%;
  background-color: #f8f9fa;
  border-radius: 10px;
  padding: 20px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}
h2 {
  color: #42b983;
  font-size: 2em;
  margin-bottom: 20px;
  text-align: center;
}
.cart-list {
  list-style: none;
  padding: 0;
}
.cart-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
  padding: 10px;
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}
.item-name {
  flex: 1;
  font-size: 1.2em;
  color: #333;
}
.item-price {
  margin-left: 20px;
  font-weight: bold;
  color: #e74c3c;
}
.remove-button {
  background-color: #e74c3c;
  color: white;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s;
}
.remove-button:hover {
  background-color: #c0392b;
}
.total-price {
  font-weight: bold;
  margin-top: 20px;
  font-size: 1.2em;
  text-align: center;
  color: #42b983;
}
</style>
