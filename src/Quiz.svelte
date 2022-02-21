<script>
  import Question from './Question.svelte'
  let activeQuestion = 0
  let score = 0
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
    resetQuiz()
  }
  const nextQuestion = () => {
    activeQuestion += 1
  }
  const resetQuiz = () => {
    activeQuestion = 0
    score = 0
  }
  const setScore = () => {
    score += 100
  }
</script>

<div>
  <button on:click={handleClick}>Start new quiz</button>
  <h3>My Score: {score}</h3>
  <h4>Question #{activeQuestion + 1}</h4>
  {#await quiz}
    Loading...
  {:then data}
    {#each data.results as question, index}
      {#if index === activeQuestion}
        <Question {nextQuestion} {question} {setScore} />
      {/if}
    {/each}
  {/await}
</div>
