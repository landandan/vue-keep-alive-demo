<template>
  <div class="List">
    <div v-for="item in arr" :key="item">
      {{item}}
    </div>
  <!-- <router-link :to="{ name: 'Home' }">首页</router-link> -->
  <button @click="back">首页</button></button>
  <router-link :to="{ name: 'About' }">关于</router-link>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'List',
  data(){
    return {
      arr: [1,2,3,4,5]
    }
  },
  methods: {
    back(){
      this.$destroy('List')
      this.$router.back()
    }
  },
  beforeCreate() {
    console.log('List beforeCreate');
  },
  created() {
    console.log('List created');
  },
  beforeMount() {
    console.log('List beforeMount');
  },
  mounted() {
    console.log('List mounted');
  },
  activated() {
    console.log('arr:', this.arr)
    console.log('List activated');
  },
  deactivated() {
    console.log('List deactivated');
  },
  beforeDestroy() {
    console.log('List beforeDestroy');
  },
  destroyed() {
    console.log('List destroyed');
  },
};
</script>
