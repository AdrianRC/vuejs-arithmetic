<template>
  <div id="app">
    <h1 id="title">The Super Quiz</h1>
    <hr>
    <br>
    <transition name="switch" type="transition" mode="out-in">
      <component :is="chosenComponent" :switchComponents="switchComponents"></component>
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
    switchComponents(component) {
      this.chosenComponent = component;
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
  transform: rotateY(90deg)
}

.switch-enter-active {
  transition: all 0.5s;
}

.switch-leave-active {
  transform: rotateY(90deg);
  transition: all 0.5s;
}
</style>
