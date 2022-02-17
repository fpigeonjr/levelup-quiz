<script>
  export let quizName = 'Frank Quiz'
  let title = ''
  let a = 0
  let b = 0
  let result = ''
  let correctAnswer = 'b'
  const add = () => a + b
  const pickAnswer = (value) => {
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
  <h4>{result}</h4>
  <button on:click={() => pickAnswer('a')}>Answer A</button>
  <button on:click={() => pickAnswer('b')}>Answer B</button>
  <button on:click={() => pickAnswer('c')}>Answer C</button>
  <button on:click={() => pickAnswer('d')}>Answer D</button>
</div>
