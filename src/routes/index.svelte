<script>
  import One from "../components/One.svelte";
  import Two from "../components/Two.svelte";
  import Three from "../components/Three.svelte";
  import FourOh4 from "../components/FourOh4.svelte";

  let selected = "one";
  // To illustrate default fallback
  // let selected;
  // ----------------------
  $: console.log(selected);

  const selectionOptions = {
    one: One,
    two: Two,
    three: Three
  };

  let components = Object.keys(selectionOptions);

  $: result =
    {
      ...selectionOptions
    }[selected] || FourOh4;
</script>

<main>
  <div class="tab_container">
    {#each components as components}
    <label>
      <input type="radio" bind:group="{selected}" value="{components}" />
      {components}
    </label>
    {/each}
  </div>

  <svelte:component this="{result}" />
</main>

<style>
  main {
    max-width: 750px;
    margin: 0 auto;
  }

  .tab_container {
    background: #b3cde0;
    display: flex;
    justify-content: center;
  }

  label {
    position: relative;
    background: #005b96;
    color: #fff;
    padding: 12px;
    cursor: pointer;
  }

  label + label {
    margin-left: 18px;
  }

  input {
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0;
  }
</style>
