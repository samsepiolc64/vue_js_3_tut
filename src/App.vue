<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <MyComponentRef />
  <MyComponentReactive />
  <MyComponentComProp />
  <MyComponentWatch />
  <MyComponentConRen />
  <MyComponentVbind />
  <MyComponentVfor />
</template>

<script>
import MyComponentRef from './components/MyComponent-ref.vue'
import MyComponentReactive from './components/MyComponent-reactive.vue'
import MyComponentComProp from './components/MyComponent-computedProperties.vue'
import MyComponentWatch from './components/MyComponent-watch.vue'
import MyComponentConRen from './components/MyComponent-v-if.vue'
import MyComponentVbind from './components/MyComponent-v-bind.vue'
import MyComponentVfor from './components/MyComponent-v-for.vue'

export default {
  name: 'App',
  components: {
    MyComponentRef,
    MyComponentReactive,
    MyComponentComProp,
    MyComponentWatch,
    MyComponentConRen,
    MyComponentVbind,
    MyComponentVfor,
  }
}
</script>

<style>
body{
  background: #232323;
  color: rgb(201, 201, 201);
}
</style>