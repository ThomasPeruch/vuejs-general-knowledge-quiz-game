<template>
  <div>
    <h1 v-html="this.question"></h1>
    <button class="send" type="button">Send</button>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      question: undefined,
      incorrect_answers: [],
      correct_answer: undefined
    }
  },
  created() {
    this.axios.get('https://opentdb.com/api.php?amount=1&category=21&difficulty=easy').then((response) => {
      this.question = response.data.results[0].question
      this.incorrect_answers = response.data.results[0].incorrect_answers
      this.correct_answer = response.data.results[0].correct_answer
    })
  }
}

</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  max-width: 960px;

  input[type=radio] {
    margin: 12px 4px
  }

  button.send {
    margin-top: 12px;
    height: 40px;
    min-width: 120px;
    padding: 0 16px;
    color: #fff;
    background-color: #1867c0;
    border: 1px solid #1867c0;
    cursor: pointer;
  }
}
</style>
