<template>
  <div id="root" :style="cssProps">
    <div class="overlay" @click="leftMenuState = false"></div>
    <LeftMenu class="menu" v-model="leftMenuState" />
    <Nav class="nav" v-model="leftMenuState" />
    <div class="page">
      <NuxtPage />
    </div>
  </div>
</template>

<script>
import '@/assets/normalize.css'
import '@/assets/skeleton.css'
import '@/assets/skeleton-dark-mode.scss'
export default {
  data() {
    return {
      leftMenuState: false
    }
  },
  computed: {
    cssProps() {
      return `
        --is-menu-open: ${this.leftMenuState ? 1 : 0};
      `
    }
  }
}
</script>

<style lang="scss">
#root {
  --menu-width: 160px;
  --is-menu-closed: calc(1 - var(--is-menu-open));

  .page,
  .menu,
  .nav {
    transition: transform 0.3s cubic-bezier(0, 0, 0, 1);
  }

  .page {
    transform: translateX(
      calc(var(--is-menu-open) * calc(var(--menu-width) / 2))
    );
    margin-top: calc(var(--nav-height) + var(--border-width));
    overflow: overlay;
    height: calc(
      100vh - calc(var(--nav-height) + calc(var(--border-width) * 2))
    );
    z-index: 1;
    position: relative;
    padding-right: var(--border-width);
  }

  .overlay {
    height: 100%;
    position: absolute;
    left: 0;
    top: 0;
    z-index: 2;
    width: calc(var(--is-menu-open) * 100%);
    //backdrop-filter: blur(10px);
  }

  .menu {
    transform: translateX(
      calc(var(--is-menu-closed) * calc(100% - var(--border-width)) * -1)
    );
    box-shadow: 0 0 calc(var(--is-menu-open) * 250px) 0px black;
    z-index: 4;
  }

  @media screen and (min-width: 1100px) {
    .page {
      transform: translateX(var(--menu-width));
      width: calc(100% - calc(var(--menu-width)));
    }

    .menu {
      transform: translateX(0);
      box-shadow: none;
    }

    .overlay {
      display: none;
    }
  }
}
</style>
