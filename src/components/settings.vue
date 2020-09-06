<template lang="pug">
aside.settings
  svg.settings__button(width="25", height="25", viewBox="0 0 50 50", fill="none",
    xmlns="http://www.w3.org/2000/svg", @click="open"
  )
    path(fill-rule="evenodd", clip-rule="evenodd", d=`M23.431 50h3.138a4.608 4.608 0
      004.603-4.603v-1.061a20.2 20.2 0 003.134-1.301l.752.751a4.602 4.602 0 006.51
      0l2.218-2.217c1.773-1.771 1.824-4.69 0-6.51l-.752-.753a20.185 20.185 0
      001.302-3.134h1.061A4.608 4.608 0 0050 26.569v-3.138a4.608 4.608 0
      00-4.603-4.603h-1.061a20.181 20.181 0 00-1.301-3.134l.751-.752c1.824-1.822 1.773-4.74
      0-6.51L41.57 6.214c-1.77-1.772-4.688-1.825-6.51 0l-.753.752a20.184 20.184 0
      00-3.134-1.302V4.603A4.608 4.608 0 0026.569 0h-3.138a4.608 4.608 0
      00-4.603 4.603v1.061c-1.079.345-2.127.78-3.134 1.301l-.752-.751a4.602 4.602 0 00-6.51
      0L6.214 8.43c-1.773 1.771-1.824 4.69 0 6.51l.752.753a20.19 20.19 0 00-1.302
      3.134H4.603A4.608 4.608 0 000 23.431v3.138a4.608 4.608 0 004.603 4.603h1.061c.345
      1.08.78 2.127 1.301 3.134l-.751.752c-1.824 1.822-1.773 4.74 0 6.51l2.217 2.218c1.77 1.772
      4.688 1.825 6.51 0l.753-.752a20.18 20.18 0 003.134 1.302v1.061A4.608 4.608 0 0023.431
      50zm-2.772-8.184a17.27 17.27 0 01-4.476-1.858c-.708-.419-1.433-.123-1.781.225l-1.533
      1.533a1.673 1.673 0 01-2.366 0l-2.219-2.22a1.673 1.673 0 010-2.366l1.533-1.532a1.465
      1.465 0 00.225-1.781 17.267 17.267 0 01-1.858-4.476 1.465 1.465 0 00-1.418-1.099H4.603c-.923
      0-1.673-.75-1.673-1.673v-3.138c0-.923.75-1.673 1.673-1.673h2.163c.668 0 1.251-.452
      1.418-1.099a17.263 17.263 0 011.858-4.476 1.465 1.465 0 00-.225-1.781l-1.533-1.533a1.673
      1.673 0 010-2.366l2.22-2.219a1.673 1.673 0 012.366 0l1.532 1.533a1.465 1.465 0 001.781.225
      17.266 17.266 0 014.476-1.858 1.465 1.465 0 001.099-1.418V4.603c0-.923.75-1.673
      1.673-1.673h3.138c.923 0 1.673.75 1.673 1.673v2.163c0 .668.452 1.251 1.1 1.418 1.57.406
      3.076 1.03 4.475 1.858.575.34 1.309.248 1.781-.225l1.533-1.533a1.673 1.673 0
      012.366.001l2.219 2.22a1.673 1.673 0 010 2.365l-1.533 1.532a1.465 1.465 0 00-.225
      1.781 17.27 17.27 0 011.858 4.476c.167.647.75 1.099 1.418 1.099h2.163c.923 0
      1.673.75 1.673 1.673v3.138c0 .923-.75 1.673-1.673 1.673h-2.163c-.668 0-1.251.452-1.418
      1.099a17.266 17.266 0 01-1.858 4.476 1.465 1.465 0 00.225 1.781l1.533 1.533a1.673 1.673
      0 010 2.366l-2.22 2.219a1.673 1.673 0 01-2.366 0l-1.532-1.533a1.465 1.465 0 00-1.781-.225
      17.27 17.27 0 01-4.476 1.858 1.465 1.465 0 00-1.099 1.418v2.163c0 .923-.75 1.673-1.673
      1.673h-3.138c-.922 0-1.673-.75-1.673-1.673v-2.163c0-.668-.452-1.251-1.099-1.418zM14.121
      25c0 5.999 4.88 10.879 10.879 10.879S35.879 30.999 35.879 25 30.999 14.121 25 14.121 14.121
      19.001 14.121 25zm2.93 0c0-4.383 3.566-7.95 7.949-7.95s7.95 3.567 7.95 7.95-3.567 7.95-7.95
      7.95-7.95-3.567-7.95-7.95z
    `)
  transition(name="fade")
    .settings-popup(v-if="show")
      .settings-popup__overlay(@click="close")
      section.settings-popup__window
        header.settings-popup__header
          .settings-popup__title Настройки
          svg.settings-popup__close(xmlns="http://www.w3.org/2000/svg", fill="none",
            viewBox="0 0 50 50", @click="close")
            path(d=`M29.58 25L49.05 5.53a3.235 3.235 0 000-4.58 3.236 3.236 0 00-4.58
              0L25 20.42 5.53.95a3.236 3.236 0 00-4.58 0 3.235 3.235 0 000 4.58L20.42 25 .95
              44.47a3.235 3.235 0 000 4.58 3.23 3.23 0 002.29.949 3.23 3.23 0 002.29-.95L25
              29.58l19.47 19.47a3.23 3.23 0 002.29.949 3.23 3.23 0 002.29-.95 3.235 3.235 0
              000-4.58L29.58 25z
            `)
        main.settings-popup__content
          textarea.settings-popup__textarea(v-model="json", placeholder="JSON of quest",
            :class="{ 'settings-popup__textarea-invalid': invalid }", @keydown="change")
          .settings-popup__textarea__message &nbsp;
            span(v-if="invalid") {{ error }}
        footer.settings-popup__footer
          btn(@click="save") Сохранить
</template>

<script>
import Btn from './button';

export default {
  name: 'Settings',
  components: {
    Btn,
  },
  props: {
    value: {
      type: Array,
      default: () => ([]),
      required: false,
    },
  },
  data: () => ({
    show: false,
    json: '',
    invalid: false,
    error: '',
  }),
  watch: {
    value(newValue) {
      this.json = JSON.stringify(newValue, null, 2);
    },
  },
  mounted() {
    this.json = JSON.stringify(this.value, null, 2);
  },
  methods: {
    resetAll() {
      this.json = JSON.stringify(this.value, null, 2);
      this.error = '';
      this.invalid = false;
    },
    change() {
      this.error = '';
      this.invalid = false;
    },
    open() {
      this.resetAll();
      this.show = true;
    },
    close() {
      this.show = false;
    },
    save() {
      try {
        const result = JSON.parse(this.json);
        this.$emit('input', result);
        this.$emit('save');
        this.close();
      } catch (e) {
        this.error = 'Невалидный JSON!';
        this.invalid = true;
      }
    },
  },
};
</script>

<style lang="scss">
.fade-enter-active, .fade-leave-active {
  transition: opacity .2s ease;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}

.settings {
  &__button {
    position: fixed;
    top: 1rem; right: 1rem;
    cursor: pointer;
    transition: all .2s;
    path {
      fill: var(--primary-text);
    }
    &:hover {
      transform: rotate(-90deg);
    }
  }
  &-popup {
    position: fixed;
    top: 0; bottom: 0;
    right: 0; left: 0;
    z-index: 3;
    display: flex;
    flex-direction: row;
    justify-content: stretch;
    align-items: stretch;
    &__overlay {
      position: fixed;
      top: 0; bottom: 0;
      right: 0; left: 0;
      background-color: var(--overlay-color);
      z-index: 1;
    }
    &__window {
      position: relative;
      z-index: 2;
      margin: auto;
      min-width: 30vmin;
      width: 90%;
      max-height: 100%;
      overflow-x: auto;
      overflow-y: auto;
      background-color: var(--primary-text);
      padding: 2.5vmin 5vmin;
      border-radius: .25rem;
    }
    &__header {
      margin-bottom: 3vmin;
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      align-items: center;
    }
    &__content {
      display: flex;
      flex-direction: column;
      justify-content: flex-start;
      align-items: flex-start;
    }
    &__footer {
      margin-top: 3vmin;
      display: flex;
      flex-direction: row;
      justify-content: flex-end;
      align-items: center;
    }
    &__textarea {
      max-width: 100%;
      min-width: 100%;
      width: 100%;
      min-height: 30vmin;
      font-size: 2vmin;
      &-invalid {
        box-shadow: 0 0 .25rem .5rem rgba(255, 80, 80, .5);
      }
      &__message {
        display: flex;
        flex-direction: row;
        justify-content: flex-start;
        align-items: center;
        width: 100%;
        min-height: 7.5vmin;
        font-size: 2.5vmin;
        font-weight: bold;
        color: rgb(255, 80, 80);
      }
    }
    &__title {
      font-size: 7vmin;
      font-weight: bold;
      color: var(--app-background);
    }
    &__close {
      width: 5vmin;
      height: 5vmin;
      transition: all .2s;
      path {
        fill: var(--app-background);
      }
      &:hover {
        transform: rotate(90deg);
      }
      &:active {
        transform: rotate(90deg) scale(.9);
      }
    }
  }
}
</style>
