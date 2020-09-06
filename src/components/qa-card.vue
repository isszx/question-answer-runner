<template lang="pug">
.qa-card(:class=`{
    'qa-card_pop': inCard,
    'qa-card_leave': inLeave,
    'qa-card_hidden': !inCard && !inLeave && !inActive,
  }`)
    h1
      slot
    .button-group(:class="{ 'button-group_row': buttonsRow, 'button-group_col': buttonsCol }")
      slot(name="buttons")
</template>

<script>
export default {
  name: 'QaCard',
  props: {
    inCard: {
      type: Boolean,
      default: false,
      required: false,
    },
    inLeave: {
      type: Boolean,
      default: false,
      required: false,
    },
    inActive: {
      type: Boolean,
      default: false,
      required: false,
    },
    buttonsRow: {
      type: Boolean,
      default: false,
      required: false,
    },
    buttonsCol: {
      type: Boolean,
      default: false,
      required: false,
    },
  },
};
</script>

<style lang="scss">
@keyframes bounceIn {
  0% { transform: scale(0, 0); }
  70% { transform: scale(1.2, 1.2); }
  100% { transform: scale(1, 1); }
}

@keyframes leave {
  100% { transform: translate(-100vw, 100vh) rotate(360deg) scale(0, 0); }
}

.qa-card {
  background-color: var(--primary-text);
  border-radius: .5rem;
  padding: .75rem;
  margin: 0 auto;
  h1 {
    color: var(--input-background);
  }
  &_pop {
    animation: bounceIn 0.4s ease-out;
  }
  &_leave {
    animation: leave 1.5s linear;
  }
  &_hidden {
    transform: scale(0);
    opacity: 0;
  }
  @media (min-width: 700px) {
    padding: 1.75rem;
    max-width: 90%;
  }
  @media (min-width: 800px) {
    max-width: 80%;
  }
  @media (min-width: 900px) {
    max-width: 75%;
  }
  @media (min-width: 1000px) {
    max-width: 70%;
  }
}

.button-group {
  padding: 1.25rem 0;
  display: flex;
  &_row {
    flex-direction: row;
    justify-content: center;
    align-items: center;
    * + * {
      margin-left: 1rem;
      @media (min-width: 700px) {
        margin-left: 3rem;
      }
    }
  }
  &_col {
    flex-direction: column;
    justify-content: center;
    align-items: center;
    * + * {
      margin-top: 1rem;
    }
  }
}
</style>
