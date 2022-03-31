<template>
  <div class="cart-item-card">
    <div class="header">
      <h3>{{ product.name }}</h3>
      <h4>In Cart: {{ product.quantity }} pieces</h4>
      <h4>Total Cost: ${{ item_cost.toFixed(2) }}</h4>
    </div>

    <p>{{ description }}</p>
    <div class="button-container">
      <button class="remove" @click="removeFromCart()">Remove</button>
      <button class="add" @click="addToCart()">Add</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["product"],
  computed: {
    description() {
      return this.product.description.substring(0, 120);
    },
    item_cost() {
      return this.product.price * this.product.quantity;
    },
  },
  methods: {
    removeFromCart() {
      this.$store.commit("removeFromCart", this.product);
    },
    addToCart() {
      this.$store.commit("addToCart", this.product);
    },
  },
};
</script>

<style lang="scss"  scoped>
div.cart-item-card {
  display: flex;
  flex-direction: column;
}
.cart-item-card {
  width: 40%;
  margin: 1%;
  background-color: white;
  box-shadow: 0 0 5px grey;
  border-radius: 5px;
  padding: 10px;
  text-align: center;
  .header {
    display: flex;
    justify-content: space-around;
  }
}
.button-container {
  button {
    width: 150px;
    border: none;
    padding: 10px;
    border-radius: 5px;
    margin: 0 5px 50px 5px;
    cursor: pointer;
    background-color: orange;
    color: white;
    font-size: 0.9rem;
  }
}
</style>