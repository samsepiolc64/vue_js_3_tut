<template>
  <div>
    <p class="header">v-if i v-show, conditional rendering</p>
    <p>Masks: {{masks}}</p>
    <p v-if="masks">dostepne</p>
    <p v-else>niedostepne</p>
    <button @click="buyMask" v-if="masks">Buy a mask</button>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  name: "MyComponent-conRend",
  setup() {
    const masks = ref(5);

    function buyMask() {
        masks.value--;
    }
    return {masks, buyMask};
  },
};
</script>

<style lang="scss" scoped>
.header {
  font-size: 19px;
  color: aqua;
}
</style>