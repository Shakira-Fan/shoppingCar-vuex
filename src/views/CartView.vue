<template>
  <div>
    <h1>Your Cart</h1>
    <div class="your-cart">
      <CartItemCard
        v-for="product in products"
        :key="product.id"
        :product="product"
      />
      <CartSummaryPaymentCard />
    </div>
  </div>
</template>

<script>
import CartItemCard from "@/components/cart/CartItemCard";
import CartSummaryPaymentCard from "@/components/cart/CartSummaryPaymentCard";

export default {
  components: {
    CartItemCard,
    CartSummaryPaymentCard,
  },
  computed: {
    products() {
      return this.$store.getters.cartItems;
    },
  },
};
</script>

<style lang="scss">
div.your-cart {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
h1 {
  text-align: center;
}
</style>