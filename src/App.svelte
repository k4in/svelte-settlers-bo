<script lang="ts">
  let counter = $state(0);

  function increment() {
    counter += 1;
  }

  function test() {
    console.log('test');
    const lalala = 38;
  }
</script>

<main>
  <button onclick={increment}>Counter: {counter}</button>
  <button onclick={() => (counter = 0)}>Reset</button>
  <p>
    <label>
      Warum <input type="text" />
    </label>
  </p>
  <p>Hello noch ein test</p>
  <form>
    <label>
      <input type="number" />
      Warum machen wir hier keine Nummer?
    </label>
    <label><textarea>Was ist denn hier eigentlich los?</textarea></label>
  </form>
</main>
