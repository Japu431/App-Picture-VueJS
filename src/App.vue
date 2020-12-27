<template>
  <div class="corpo">

    <MeuMenu :rotas="routes" />

    <transition name="page">
      <router-view></router-view>    
    </transition>
    
  </div>
</template>

<script>
import { routes } from "./routes.js";
import Menu from "./components/shared/menu/Menu.vue";

export default {
  components: {
    MeuMenu: Menu,
  },
  data() {
    return {
      routes,
    };
  },
};
</script>

<style scoped>
.center {
  text-align: center;
}

.page-enter,
.page-leave-active {
  opacity: 0;
}

.page-enter-active,
.page-leave-active {
  transition: opacity 0.5s;
}
</style>
