<script setup>
import { RouterView } from 'vue-router';
import AsideMenu from '../components/asideMenu.vue';

// export default {
//     name: "ElementsLayout",
//     components: { AsideBar }
// }
</script>
<template>
  <section class="d-flex elements__section display--flex">
    <AsideMenu />
    <main class="elements__main">
      <RouterView />
    </main>
  </section>
</template>


<style lang="scss" scoped>
  .elements {
    &__section {
      position: relative;
      background-color: var(--vt-c-black-soft);
    }
    &__main {
      position: relative;
      width: 100%;
      height: 5000px;
    }
  }
</style>