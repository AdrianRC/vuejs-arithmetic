<template>
    <div id="incorrect">
      <h2 id="header">Incorrect.</h2>
      <br>
      <br>
      <button @click="switchComponents('quiz')">Continue</button>
    </div>
</template>

<script>
export default {
  props: ['switchComponents'],
};
</script>

<style scoped>

#header {
  color: darkred;
  text-align: center;
  font-size: 34px;
}

#incorrect {
    border: 1px solid gray;
    width: 40%;
    margin: 0 auto;
    height: 200px;
    background-color: lightcoral;
}

button {
  width: 25%;
  margin: 0 auto;
  display: block;
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
