<template lang="pug">
.preloader(:class="{ 'preloader_animation': value }")
  .preloader__app-ico
</template>

<script>
export default {
  name: 'PreLoader',
  props: {
    value: {
      type: Boolean,
      default: false,
      required: false,
    },
  },
};
</script>

<style lang="scss">
@keyframes load {
  0% {
    bottom: calc(100% - .25rem);
    left: 100%;
  }
  50% {
    left: -3rem;
    bottom: calc(100% - .25rem);
  }
  100% {
    left: -3rem;
    bottom: -3rem;
  }
}

@keyframes buble-logo {
  0% { transform: translate(-50%, -50%)  scale(1); }
  25% { transform: translate(-50%, -50%) scale(0.8); }
  50% { transform: translate(-50%, -50%)  scale(1.2); }
  75% { transform: translate(-50%, -50%)  scale(0.8); }
  100% { transform: translate(-50%, -50%)  scale(1); }
}

.preloader {
  position: fixed;
  top: 0; bottom: 0;
  left: 0; right: 0;
  border-radius: 1rem;
  background: #47cf73;
  z-index: 10;
  &:before {
    position: fixed;
    content: '';
    position: fixed;
    left: 0; right: 0;
    top: 0; bottom: 0;
    background: var(--app-background);
    border-radius: 1rem;
    z-index: 1;
  }
  &:after {
    content: '';
    position: fixed;
    left: .25rem; right: .25rem;
    top: .25rem; bottom: .25rem;
    border-radius: 1rem;
    background: var(--app-background);
    z-index: 2;
  }
  &_animation:before {
    animation: load 2s linear infinite;
  }
  &__app-ico {
    position: fixed;
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    width: 100px;
    height: 100px;
    background-image: url('~@/assets/favicon.svg');
    background-repeat: no-repeat;
    background-position: center;
    background-size: contain;
    z-index: 3;
    animation: buble-logo 2s linear infinite;
  }
}
</style>
