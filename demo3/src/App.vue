<template>
  <div id="app">
    <transition :name="transition">
      <keep-alive :include="keepAliveList">
        <router-view></router-view>
      </keep-alive>
    </transition>
  </div>
</template>
<script>
import { routes } from './router/index'
export default {
  name: 'app',
  data() {
    return {
      transition: 'slide-right',
      routerArr: [{ name: 'Home' }],
    };
  },
  computed: {
    keepAliveList() {
      const keeps = routes.filter(page => (page.meta && page.meta.keepAlive))
      return keeps.map(page => page.name)
    }
  },
  watch: {
    $route(to, from) {
      const toIndex = this.routerArr.findIndex(item => item.name == to.name);
      const fromIndex = this.routerArr.findIndex(item => item.name == from.name);

      if (toIndex > -1) {
        this.transition = 'slide-right';
        this.routerArr.splice(fromIndex);
      } else {
        this.transition = 'slide-left';
        this.routerArr.push(to);
      }
    },
  },
};
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

.slide-right-enter-active,
.slide-right-leave-active,
.slide-left-enter-active,
.slide-left-leave-active {
  will-change: transform;
  transition: all 0.3s;
  position: absolute;
  width: 100%;
  left: 0;
}

.slide-right-enter {
  transform: translateX(-100%);
}

.slide-right-leave-active {
  transform: translateX(100%);
}

.slide-left-enter {
  transform: translateX(100%);
}

.slide-left-leave-active {
  transform: translateX(-100%);
}
</style>
