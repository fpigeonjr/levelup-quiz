<script>
  import Question from './Question.svelte'
  let activeQuestion = 0
  const getQuiz = async () => {
    const res = await fetch(
      'https://opentdb.com/api.php?amount=10&category=15&type=multiple'
    )
    const quiz = await res.json()
    return quiz
  }

  let quiz = getQuiz()

  const handleClick = () => {
    quiz = getQuiz()
  }
  const nextQuestion = () => {
    activeQuestion += 1
  }
</script>

<div>
  <button on:click={handleClick}>Start new quiz</button>
  <h3>My Score: 0</h3>
  <h4>Question #{activeQuestion + 1}</h4>
  {#await quiz}
    Loading...
  {:then data}
    {#each data.results as question, index}
      {#if index === activeQuestion}
        <Question {nextQuestion} {question} />
      {/if}
    {/each}
  {/await}
</div>
