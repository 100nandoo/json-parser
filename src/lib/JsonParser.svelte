<script>
  import JsonTree from "svelte-json-tree";
  let result = {};
  let input = "";

  const handleInput = () => {
    result = JSON.parse(input);
  };
</script>

<div class="json-parser">
  <div class="">
    <textarea name="input" class="textarea" cols="40" rows="5" bind:value={input} on:input={handleInput}></textarea>
  </div>
  <div class="output">
    <JsonTree value={result} defaultExpandedLevel={1} />
  </div>
</div>

<style>
  .output {
    width: 100%;
  }
  .json-parser {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
  }
</style>
