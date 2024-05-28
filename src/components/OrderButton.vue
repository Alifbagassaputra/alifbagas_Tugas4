<template>
  <button @click="addToCart" class="add-button">Add to Cart</button>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true
    }
  },
  methods: {
    addToCart() {
      this.$emit('addToCart', this.item);
    }
  }
};
</script>

<style scoped>
.add-button {
  background-color: #42b983;
  color: white;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 5px;
  font-size: 1em;
  transition: background-color 0.3s;
}
.add-button:hover {
  background-color: #35495e;
}
</style>
