<template>
  <div>
    <p class='header'>reactive</p>
    <button @click="makeOrder">go</button>
    <p>quantity: {{ quantity }}</p>
    <p>price: {{ price }}</p>
    <p>totalPrice: {{ totalPrice }}</p>
    <p>tax: {{ tax }}</p>
  </div>
</template>

<script>
import { toRefs, reactive } from "vue";
export default {
  name: "MyComponent-reactive",
  setup() {

    const state = reactive({
        quantity: 1,
        price: 100,
        totalPrice: 0,
        tax: 0
    })

    function makeOrder() {
      state.price++;
      state.totalPrice = state.quantity*state.price;
      state.tax = state.totalPrice*0.23;
    }

    return { ...toRefs(state), makeOrder };
  },
};
</script>

<style lang="scss" scoped>
    .header {
        font-size: 19px;
        color: aqua;
    }
</style>