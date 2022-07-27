<script>
  import { fade } from "svelte/transition";
  let count = 0;
  const countUp = (e) => (count += Number(e.target.value));
  const countDown = (e) => (count -= Number(e.target.value));
  const countDiv = (e) => Math.round((count /= Number(e.target.value)));
  const countMulti = (e) => Math.round((count *= Number(e.target.value)));
  const clearVal = (e) => {
    setInterval(() => {
      e.target.value = null;
    }, 3000);
  };
</script>

<button on:click={() => count++}>
  count is {count}
</button>
<fieldset>
  <input
    name="up"
    type="number"
    on:input={countUp}
    on:blur={clearVal}
    placeholder="counting up"
  />
  <label for="up">Addition</label>
  <input
    name="down"
    type="number"
    on:input={countDown}
    on:blur={clearVal}
    placeholder="counting down"
  />
  <label for="down">Substraktion</label>
  <input
    name="div"
    type="number"
    on:input={countDiv}
    on:blur={clearVal}
    placeholder="counting division"
  />
  <label for="div">Division</label>
  <input
    name="multi"
    type="number"
    on:input={countMulti}
    on:blur={clearVal}
    placeholder="counting division"
  />
  <label for="multi">Multiplikation</label>
</fieldset>

<div class="result">
  <h1 class:red={count === 0}>{count}</h1>
</div>

<button on:click={() => (count = 0)}>Reset</button>

<style>
  .red {
    color: red;
  }
  fieldset {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
    background: linear-gradient(to top right, lightgreen, yellow);
    padding: 3rem;
    border-radius: 10px;
    border: none;
  }
  label {
    color: lightcoral;
    margin: 0.5rem 0;
  }
  input {
    color: brown;
  }
  .result {
    background-color: antiquewhite;
    border-radius: 10px;
    padding: 1rem;
    margin: 1rem auto;
  }
</style>
