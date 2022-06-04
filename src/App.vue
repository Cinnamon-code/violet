<template>
  <div id="app">
    <el-menu :default-active="$route.path"
             router
             mode="horizontal"
             active-text-color="#42b983">
      <el-menu-item v-for="link in links" :key="link.id" :index="link.to">
        {{ link.name }}
      </el-menu-item>
    </el-menu>
    <transition name="fade">
      <router-view/>
    </transition>
  </div>
</template>
<script>
export default {
  name: 'App',
  data() {
    return {
      links: [
        {id: 0, name: 'Home', to: '/'},
        {id: 1, name: 'Gallery', to: '/gallery'},
        {id: 2, name: 'Cinema', to: '/cinema'}
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

.el-menu {
  display: flex;
  font-weight: bold;
}

.el-menu-item {
  flex: 1;
  text-align: center;
}

.fade-enter, .fade-leave-to {
  transform: translateY(30px);
  opacity: 0;
}

.fade-enter-active, .fade-leave-active {
  transition: all .3s ease;
}
</style>
