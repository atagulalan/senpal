<template>
  <div class="nav-menu">
    <button @click="toggle" class="menu-button">
      <svg viewBox="0 0 44 44">
        <path
          fill="#FFF"
          d="M10.8 16.8c-.5 0-.5.8.1.8 7.5-.1 15.7.1 22 .3.8 0 .8-1.8 0-1.8.1 0-14.5.6-22.1.7zM33.2 27.3c.5 0 .5-.7-.1-.7-7.5.1-15.7-.1-22-.3-.8 0-.8 1.7 0 1.7-.1-.1 14.5-.6 22.1-.7z"
        />
      </svg>
    </button>
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
.nav-menu {
  width: 100%;
  height: calc(var(--nav-height) + var(--border-width));
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1;
  display: flex;
  transform: translateX(
    calc(var(--is-menu-open) * calc(var(--menu-width) - var(--border-width)))
  );
  border: var(--border-width) solid var(--border-color);

  .menu-button {
    width: auto;
    height: 100%;
    aspect-ratio: 1;
    padding: 0;
    border: none;
    margin: 0;
    overflow: hidden;
  }
}
</style>
