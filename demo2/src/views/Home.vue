<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <router-link :to="{ name: 'About' }">关于</router-link>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';

export default {
  name: 'Home',
  components: {
    HelloWorld,
  },
  beforeCreate() {
    console.log('Home beforeCreate');
  },
  created() {
    console.log('Home created');
  },
  beforeMount() {
    console.log('Home beforeMount');
  },
  mounted() {
    console.log('Home mounted');
  },
  activated() {
    console.log('Home activated');
  },
  deactivated() {
    console.log('Home deactivated');
  },
  beforeDestroy() {
    console.log('Home beforeDestroy');
  },
  destroyed() {
    console.log('Home destroyed');
  },
};
</script>
