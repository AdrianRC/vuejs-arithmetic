<template>
  <div id="app">
    <h1 id="title">The Super Quiz</h1>
    <hr>
    <br>
    <button @click="switchComponents">hey</button>
    <transition name="switch" type="transition" mode="out-in">
      <component :is="chosenComponent"></component>
    </transition>
  </div>
</template>

<script>
import Quiz from './components/Quiz';
import Correct from './components/Correct';

export default {
  components: {
    Quiz,
    Correct,
  },
  data() {
    return {
      chosenComponent: 'quiz',
    };
  },
  methods: {
    switchComponents() {
      /* eslint-disable no-constant-condition  */
      if (this.chosenComponent === 'quiz') {
        this.chosenComponent = 'correct';
      } else {
        this.chosenComponent = 'quiz';
      }
    },
  },
};
</script>

<style scoped>
hr {
  width: 80%;
}

#title {
  text-align: center;
}

.switch-enter {
  transform: rotate3d(0, 1, 0, 90deg);
}

.switch-enter-active {
  transition: all 0.5s;
}

.switch-leave {
}

.switch-leave-active {
  transform: rotate3d(0, 1, 0, -90deg);
  transition: all 0.5s;
}
</style>
