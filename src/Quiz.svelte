<script>
  export let quizName = 'Frank Quiz'
  let title
  let a = 0
  let b = 0
  let result
  let answers = ['a', 'b', 'c', 'd']
  let correctAnswer = 'b'
  const add = () => a + b
  const pickAnswer = (value) => {
    console.log(value)
    if (value === correctAnswer) {
      return (result = 'Correct')
    }
    result = 'Oops, wrong answer'
  }
</script>

<div>
  <h2>{quizName}</h2>
  <p>{title}</p>
  <input bind:value={title} type="text" />
  <br />
  <input type="number" bind:value={a} />
  <input type="number" bind:value={b} />
  <p>Sum</p>
  <p>Total is {add(a, b)}</p>
  {#if result}
    <h4>{result}</h4>
  {:else}
    <h4>Please pick an answer</h4>
  {/if}
  {#each answers as answer}
    <button on:click={() => pickAnswer(answer)}
      >Answer {answer.toUpperCase()}</button
    >
  {/each}
</div>
