<template lang="pug">
section#app
  pre-loader(v-if="preloader" v-model="loading")

  settings(v-model="inputJSON", @save="startApp")

  qa-card(:inCard="inCard", :inLeave="inLeave", :inActive="inActive", buttons-row)
    template(#default) {{ inputJSON[step].question }}
    template(#buttons)
      template(v-for="answer in inputJSON[step].answers")
        answer-button(@click="result($event, answer, inputJSON[step].question)", :disabled="block")
          span {{ answer }}

</template>

<script>
import AnswerButton from './components/button';
import PreLoader from './components/preloader';
import QaCard from './components/qa-card';
import Settings from './components/settings';

const sleep = (time) => new Promise((resolve) => setTimeout(resolve, time * 1000));

export default {
  name: 'QAApplication',
  components: {
    AnswerButton,
    PreLoader,
    QaCard,
    Settings,
  },
  data: () => ({
    inputJSON: [{
      question: 'Правда что шашки появились на много раньше шахмат?', // да
      answers: ['Да', 'Нет'],
    }, {
      question: 'Сумма чисел на противоположных сторонах игральной кости всегда четная?', // нет
      answers: ['Да', 'Нет'],
    }, {
      question: 'Масса мячика для игры в настольный теннис меньше 5 граммов?', // да
      answers: ['Да', 'Нет'],
    }, {
      question: 'Белый порошок, которым мажут руки гимнасты — это мел?', // нет
      answers: ['Да', 'Нет'],
    }, {
      question: 'Херлинг — это ирландский травяной хоккей?', // да
      answers: ['Да', 'Нет'],
    }],

    results: [],

    step: 0,

    block: false,

    inCard: false,
    inLeave: false,
    inActive: false,

    preloader: true,
    loading: false,
  }),

  mounted() {
    this.startApp();
  },

  methods: {
    resetData() {
      this.results = [];
      this.step = 0;
      this.block = false;
      this.inCard = false;
      this.inLeave = false;
      this.inActive = false;
      this.preloader = true;
    },
    async startApp() {
      this.resetData();
      this.loading = false;
      await sleep(0.2);
      this.loading = true;
      await sleep(2);
      this.preloader = false;
      await sleep(0.2);
      this.inCard = true;
      await sleep(0.5);
      this.inCard = false;
      this.inActive = true;
    },
    async result(e, answer, question) {
      // check step and blocker
      if (this.step > this.inputJSON.length - 1 || this.block) {
        return;
      }
      // if current step is not last play leave animation
      if (this.step !== this.inputJSON.length - 1) {
        this.inLeave = true;
        await sleep(1.5);
      }

      // push answer to json
      this.results.push({
        question,
        answer,
      });

      // check is question is last?
      if (this.step === this.inputJSON.length - 1) {
        this.block = true;
        global.console.log('results:', {
          asObject: this.results,
          asString: JSON.stringify(this.results),
        });
        return;
      }

      // add 1 to step for go to next question
      this.step += 1;

      // drop focus from button
      e.target.blur();

      // disable class leave
      this.inLeave = false;
      // switch active to false
      this.inActive = false;
      await sleep(0.2);
      // start pupin animation
      this.inCard = true;

      // wait playng animation
      await sleep(0.5);
      // switch activ to true
      this.inActive = true;
      this.inCard = false;
    },
  },
};
</script>

<style lang="scss">
:root {
  --fonts: 'Rubik', 'Helvetica Neue', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', sans-serif;
  font-family: var(--fonts);

  font-size: 15px;
  line-height: 1.5;

  --input-background: #252830;
  --button-background: #444857;
  --primary-text: #fff;
  --secondary-text: #c7c9d3;
  --placeholder-text: #868ca0;

  --overlay-color: rgba(0, 0, 0, .9);

  --app-background: #131417;

  color: var(--primary-text);

  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

* {
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
  box-sizing: border-box;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  overflow-x: hidden;
  height: 100%;
  -webkit-overflow-scrolling: touch;
}

body {
  position: relative;
  overflow-x: hidden;
  overflow-y: auto;
  height: 100%;
  background: var(--app-background);
  min-width: 320px;
}

#app {
  position: relative;
  margin: 1.35rem;
  height: calc(100% - 2.7rem);
  display: flex;
  flex-direction: column;
  justify-content: center;
  &:after {
    content: '';
  }
  @media (min-width: 700px) {
    margin: 3rem;
    height: calc(100% - 6rem);
  }
}

h1, h2, h3, h4, h5, h6 {
  color: var(--primary-text);
}

h1 {
  /* 1680 = 71 */
  font-size: 7vmin;
  text-align: center;
}

p {
  font-size: 1.2rem;
  margin-bottom: 2rem;
  color: var(--secondary-text);
}

p, pre, blockquote {
  margin: 0 0 1em 0;
}

a {
  text-decoration: none;
}

%--input {
  font-family: var(--fonts);
  -webkit-appearance: none;
  outline: 0;

  padding: .4em .4em .4em .4em;
  text-indent: 0;

  font: inherit;

  background: var(--input-background);
  color: var(--primary-text);

  border: .2rem solid var(--input-background);
  border-radius: .25rem;
}

%--placeholder {
  color: var(--placeholder-text);
  text-overflow: ellipsis
}

input {
  &[type='name'], &[type='text'], &[type='email'], &[type='password'], &[type='tel'],
  &[type='date'], &[type='datetime-local'], &[type='search'], &[type='url'], &[type='number'] {
    @extend %--input;
    &::placeholder {
      @extend %--placeholder;
    }
  }
}

textarea {
  @extend %--input;
  &::placeholder {
    @extend %--placeholder;
  }
}
</style>
