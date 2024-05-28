<template>
  <div class="menu">
    <h2>Menu</h2>
    <ul class="menu-list">
      <li v-for="item in menuItems" :key="item.id" class="menu-item card">
        <img :src="item.image" :alt="item.name" class="item-image">
        <div class="item-details">
          <span class="item-name">{{ item.name }}</span>
          <span class="item-price">${{ item.price }}</span>
          <OrderButton :item="item" @addToCart="addItemToCart" />
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import OrderButton from './OrderButton.vue';

export default {
  data() {
    return {
      menuItems: [
        { id: 1, name: 'Burger', price: 10, image: 'https://media.istockphoto.com/id/1398630614/id/foto/burger-keju-bacon-di-atas-roti-panggang.jpg?s=2048x2048&w=is&k=20&c=mzDpofAAoknx5BYtPQUtXYVJ81sg9bMk9U4tD17vAfc=' },
        { id: 2, name: 'Pizza', price: 12, image: 'https://media.istockphoto.com/id/1442417585/id/foto/orang-yang-mendapatkan-sepotong-pizza-pepperoni-murahan.jpg?s=2048x2048&w=is&k=20&c=cfoDtRdZYhMLMZXqYtY-jYGChbbBEiFGrAFps7nHIwc=' },
        { id: 3, name: 'Salad', price: 8, image: 'https://media.istockphoto.com/id/1349067702/id/foto/salad-yunani-dengan-saus-vinaigrette-atasnya-dengan-ayam-panggang.jpg?s=2048x2048&w=is&k=20&c=uGTlDHV7u551xuTSyqSUd2wmLNOU2ncmINF0FpPwOe8=' }
      ]
    };
  },
  components: {
    OrderButton
  },
  methods: {
    addItemToCart(item) {
      this.$emit('itemAdded', item);
    }
  }
};
</script>

<style scoped>
.menu {
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
.menu-list {
  list-style: none;
  padding: 0;
}
.menu-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 20px;
  padding: 15px;
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.2s, box-shadow 0.2s;
}
.menu-item:hover {
  transform: scale(1.05);
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.2);
}
.item-image {
  width: 100%;
  height: auto;
  border-radius: 10px;
  margin-bottom: 10px;
}
.item-details {
  text-align: center;
}
.item-name {
  display: block;
  font-size: 1.4em;
  font-weight: bold;
  color: #333;
  margin-bottom: 5px;
}
.item-price {
  display: block;
  font-size: 1.2em;
  color: #e74c3c;
  margin-bottom: 10px;
}
</style>
