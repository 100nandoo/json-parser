<script>
  import Prism from 'prismjs'
  import 'prismjs/components/prism-json'
  import 'prismjs/plugins/line-numbers/prism-line-numbers'
  import 'prismjs/plugins/line-numbers/prism-line-numbers.css'
  import 'prismjs/plugins/match-braces/prism-match-braces'
  import 'prismjs/plugins/match-braces/prism-match-braces.css'
  import { onMount } from 'svelte'
  import '../css/prism-dracula.css'

  let input = ''
  let formatted = ''

  const handleInput = () => {
    try {
      formatted = JSON.stringify(JSON.parse(input), null, 2)
    } catch (err) {
      formatted = input
    }

    let result_element = document.querySelector('#highlighting-content')
    result_element.innerHTML = formatted
    Prism.highlightElement(result_element)
  }

  $: if (input) {
    handleInput()
  }
  onMount(() => {
    input = `{"hello":{"count":13},"world":[{"type":"articles","id":"3","attributes":{"title":"JsonParser","body":"Theshortestarticle.Ever.","status":true,"updated":"2015-05-22T14:56:28.000Z"}}],"links":{"self":"www.halim.dev","first":"json.halim.dev"}}`
  })
</script>

<div class="json-parser p-2 grid grid-cols-1 lg:grid-cols-2 bg-slate-400">
  <div class="pb-2 lg:pr-2">
    <label for="parser-input">
      <textarea name="input" class="parser-input textarea textarea-primary" placeholder="Insert your json here..." bind:value={input} on:input={handleInput} />
    </label>
  </div>

  <div class="parser-result rounded-md">
    <pre id="highlighting  "><code class="open language-json match-braces line-numbers" id="highlighting-content" /></pre>
  </div>
</div>

<style>
  .textarea {
    font-family: 'Fira Mono';
    font-size: 12px;
    line-height: 1.5;
  }
  .parser-input {
    float: left;
    min-height: 500px;
    position: relative;
    overflow: visible;
    width: 100%;
  }

  pre {
    font-family: 'Fira Mono';
    font-size: 12px;
    line-height: 1.5;
    min-height: 500px;
  }

  .parser-result {
    float: right;
    position: relative;
    overflow: hidden;
  }

  .json-parser {
    width: 100%;
    height: 100%;
  }
</style>
