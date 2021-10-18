<template>
  <div>
    <p class="header">computed Watch</p>
    <p>
      you hame {{ shares }} shares and their value is {{ sharesValue }}$,
      bacause share price is {{ sharePrice }}$
    </p>

    <button @click="changeNumberOfShares(1)">buy one share</button>
    <button @click="changeNumberOfShares(5)">buy five shares</button>
    <button @click="changeNumberOfShares(-1)">sell one share</button>
    <button @click="changeNumberOfShares(-5)">sell five shares</button>
  </div>
</template>

<script>
import { ref, computed, watch } from "vue";
export default {
  name: "MyComponent-watch",
  setup() {
    const shares = ref(15);
    const sharePrice = ref(20);
    const sharesValue = computed(() => shares.value * sharePrice.value);

    function changeNumberOfShares(number) {
      if (shares.value + number >= 0) {
        shares.value += number;
      }
    }

    function getPrice(min, max) {
      const priceDiff = Math.floor(Math.random() * (max - min) + min);
      if (sharePrice.value + priceDiff >= 0) {
        sharePrice.value += priceDiff;
      }
    }

    watch(shares, (before, after) => {
      before > after ? getPrice(1, 5) : getPrice(-5, -1);
    });

    return { shares, sharePrice, sharesValue, changeNumberOfShares };
  },
};
</script>

<style lang="scss" scoped>
.header {
  font-size: 19px;
  color: aqua;
}
</style>