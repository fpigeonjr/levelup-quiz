<script>
  export let question
  export let nextQuestion
  export let setScore
  let isCorrect
  let isAnswered = false
  let answers = question.incorrect_answers.map((answer) => {
    return {
      answer,
      correct: false,
    }
  })
  let allAnswers = [
    ...answers,
    {
      answer: question.correct_answer,
      correct: true,
    },
  ]
  const shuffle = (array) => {
    array.sort(() => Math.random() - 0.5)
  }
  shuffle(allAnswers)
  const checkQuestion = (correct) => {
    isCorrect = correct
    isAnswered = true
    if (isCorrect) {
      setScore()
    }
  }
</script>

<p>{@html question.question}</p>
{#if isAnswered}
  {#if isCorrect}
    <h4 class="text-green">🥳 You got it right</h4>
  {:else}
    <h4 class="text-red">You goofed up</h4>
  {/if}
{/if}

{#each allAnswers as answer}
  <button on:click={() => checkQuestion(answer.correct)}
    >{@html answer.answer}</button
  >
{/each}
<br />
{#if isAnswered}
  <button on:click={nextQuestion}>Next question</button>
{/if}

<style>
  .text-green {
    color: green;
  }
  .text-red {
    color: red;
  }
</style>
