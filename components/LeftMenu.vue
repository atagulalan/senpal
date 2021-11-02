<template>
  <div class="left-menu">
    <div class="logo">
      <img src="@/assets/logo.svg" alt="SENPAL" />
      <h1>SENPAL</h1>
    </div>

    <ul>
      <router-link to="/" custom v-slot="{ navigate, isActive }">
        <li @click="navigate" :class="{ active: isActive }">Home</li>
      </router-link>

      <router-link to="/about" custom v-slot="{ navigate, isActive }">
        <li @click="navigate" :class="{ active: isActive }">About</li>
      </router-link>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['modelValue'],
  methods: {
    toggle() {
      this.$emit('update:modelValue', !this.modelValue)
    }
  }
}
</script>

<style lang="scss">
.left-menu {
  width: var(--menu-width);
  background-color: #000000;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  z-index: 3;
  border: var(--border-width) solid var(--border-color);

  .logo {
    display: flex;
    align-items: center;
    justify-content: center;
    height: var(--nav-height);
    border-bottom: var(--border-width) solid var(--border-color);

    img {
      display: inline-block;
      width: 24px;
      height: 24px;
      margin-right: 8px;
    }

    h1 {
      font-size: 14pt;
      font-weight: 900;
      display: inline-block;
      margin: 0;
      padding: 0;
      cursor: default;
    }
  }

  ul {
    margin-right: calc(var(--border-width) * -1);

    li {
      margin-bottom: 0px;
      background: transparent;
      padding: 15px 30px;
      list-style: none;
      border-right: var(--border-width) solid var(--border-color);

      &.active {
        border-right: var(--border-width) solid var(--active-color);
        background: rgba(255, 255, 255, 0.07);
      }

      a {
        text-decoration: none;
      }
    }
  }
}
</style>
