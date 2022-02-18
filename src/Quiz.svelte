<script>
  import Question from './Question.svelte'
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
</script>

<div>
  <button on:click={handleClick}>Get New Question</button>
  {#await quiz}
    Loading...
  {:then data}
    {#each data.results as question}
      <Question {question} />
    {/each}
  {/await}
</div>
