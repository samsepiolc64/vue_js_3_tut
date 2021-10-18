<template>
  <div>
    <p class='header'>computed Properties</p>
    <button @click="makeOrder">go</button>
    <p>quantity: {{ quantity }}</p>
    <p>price: {{ price }}</p>
    <p>totalPrice: {{ totalPrice }}</p>
    <p>tax: {{ tax }}</p>
  </div>
</template>

<script>
import { toRefs, reactive, computed } from "vue";
export default {
  name: "MyComponent-computedProperties",
  setup() {

    const state = reactive({
        quantity: 1,
        price: 100,
        totalPrice: computed(() => state.price * state.quantity),
        tax: 0
    })

    function makeOrder() {
      state.price++;
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