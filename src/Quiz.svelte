<script>
  export let quizName = 'Frank Quiz'
  let title = ''
  let a = 0
  let b = 0

  const add = () => a + b
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
</div>
