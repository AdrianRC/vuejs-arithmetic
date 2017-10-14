<template>
  <div id="quiz">
    <div id="question">
      <h4>What's {{ number1 }} {{ operator }} {{ number2 }}?</h4>
    </div>
    <div id="answers">
      <button v-for="number in answers" :key="number" @click="check(number)">{{ number }}</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['switchComponents'],
  created() {
    this.populateAnswers(4);
  },
  data() {
    return {
      number1: 0,
      number2: 0,
      operator: '-',
      answers: [],
      chosenAnswer: 0,
    };
  },
  methods: {
    populateAnswers(number) {
      this.number1 = this.random(0, 101);
      this.number2 = this.random(0, 101);
      const chooseOperator = this.random(0, 2);
      this.operator = chooseOperator === 0 ? '+' : '-';
      this.chosenAnswer = this.operator === '+' ? (this.number1 + this.number2) : (this.number1 - this.number2);
      let answers = [this.chosenAnswer];
      for (let i = 0; i < number - 1; i += 1) {
        answers.push(this.findAnswer(answers));
      }
      answers = this.shuffleArray(answers);
      this.answers = answers;
    },
    random(min, max) {
      return Math.floor((Math.random() * (max - min)) + min);
    },
    findAnswer(myArr) {
      let found = 0;
      let answer;
      while (found !== -1) {
        answer = this.random(this.chosenAnswer - 10, this.chosenAnswer + 10);
        found = myArr.indexOf(answer);
      }
      return answer;
    },
    shuffleArray(array) {
      /* eslint-disable no-param-reassign */
      for (let i = array.length - 1; i > 0; i -= 1) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
      }
      return array;
    },
    check(number) {
      if (number === this.chosenAnswer) {
        this.switchComponents('correct');
      }
    },
  },
};
</script>


<style scoped>
h4 {
  margin: 0;
}

#question {
  background-color: #EEEEEE;
  text-align: center;
  border: 1px solid darkgray;
  height: 30px;
  line-height: 30px;
}

#answers {
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
}

#quiz {
  border: 1px solid gray;
  width: 40%;
  margin: 0 auto;
  height: 200px;
}

button {
  width: 25%;
  margin: 5% 12.5%;
  background-color: lightskyblue;
  border: 1px solid darkgray;
  border-radius: 8px;
  height: 30px;
  color: white;
  font-weight: 600;
  font-size: 16px;
  cursor: pointer;
}

button:focus {
  outline: none;
}
</style>
