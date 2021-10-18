<template>
  <div>
    <p class='header'>ref</p>
    <button @click="incrementPension">go</button>
    {{ pension }}
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  name: "MyComponent-ref",
  setup() {
    const pension = ref(100);

    function incrementPension() {
      pension.value++;
    }

    return { pension, incrementPension };
  },
};
</script>

<style lang="scss" scoped>
    .header {
        font-size: 19px;
        color: aqua;
    }
</style>