<template lang="pug">
button.button.button_green.button_bold(
  @click="$emit('click', $event)", :disabled="disabled", tabindex="1"
): slot
</template>

<script>
export default {
  name: 'Button',
  props: {
    disabled: {
      type: Boolean,
      default: false,
      required: false,
    },
  },
};
</script>

<style lang="scss">
.button {
  -webkit-appearance: none;
  appearance: none;
  cursor: pointer;
  user-select: none;

  outline: none;

  display: inline-block;
  position: relative;

  padding: .25rem .5rem; // 10px 16px
  border: .2rem solid transparent;
  border-radius: .25rem;

  background: var(--button-background);

  color: var(--primary-text);
  font-family: var(--fonts);
  font-size: 5vmin;
  line-height: 1.2;
  text-shadow: none;
  text-overflow: ellipsis;
  text-decoration: none;
  text-align: center;
  white-space: nowrap;

  transition: all .2s;
  &_bold {
    font-weight: 700;
  }
  &:hover {
    @media(hover: hover) and (pointer: fine) {
      filter: brightness(0.8);
    }
  }
  &:active {
    transform: translateY(-2px);
  }
  &:focus {
    box-shadow: 0 0 0 .2rem rgba(255, 255, 255, .4);
    @media (min-width: 700px) {
      box-shadow: 0 0 0 .5rem rgba(255, 255, 255, .4);
    }
  }
  &:disabled {
    color: #677;
    cursor: not-allowed;
    filter: grayscale(1);
    box-shadow: none;
    transform: none;
  }
  &_green {
    background: rgb(71, 207, 115);
    color: #000;
    &:focus {
      box-shadow: 0 0 0 .2rem rgba(71, 207, 115, .4);
      @media (min-width: 700px) {
      box-shadow: 0 0 0 .5rem rgba(71, 207, 115, .4);
    }
    }
  }
  @media (min-width: 700px) and (min-height: 460px) {
    padding: .75rem 2.75rem;
    font-size: 5vmin;
  }
}
</style>
