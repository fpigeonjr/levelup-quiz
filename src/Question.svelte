<script>
  export let question
  let answers = question.incorrect_answers
</script>

<p>{@html question.question}</p>
{#each answers as answer}
  <button>{@html answer}</button>
{/each}
