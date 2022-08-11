<script>
  import { CopyButton } from 'carbon-components-svelte'
  import 'carbon-components-svelte/css/g100.css'
  import Prism from 'prismjs'
  import 'prismjs/components/prism-json'
  import 'prismjs/plugins/line-numbers/prism-line-numbers'
  import 'prismjs/plugins/line-numbers/prism-line-numbers.css'
  import 'prismjs/plugins/match-braces/prism-match-braces'
  import 'prismjs/plugins/match-braces/prism-match-braces.css'
  import '../css/prism-dracula.css'

  let input = ''
  let formatted = ''

  const handleInput = () => {
    formatted = JSON.stringify(JSON.parse(input), null, 2)

    let result_element = document.querySelector('#highlighting-content')
    result_element.innerHTML = formatted
    Prism.highlightElement(result_element)
  }
</script>

<div class="json-parser p-2">
  <div class="pr-4">
    <textarea name="input" class="parser-input textarea textarea-primary" bind:value={input} on:input={handleInput} />
  </div>

  <div class="parser-result">
    <pre id="highlighting"><code class="open language-json match-braces line-numbers" id="highlighting-content" /></pre>
    <div class="topright mt-2">
      <CopyButton text={formatted} feedback="Copied to clipboard" />
    </div>
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
    width: 50%;
  }

  pre {
    font-family: 'Fira Mono';
    font-size: 12px;
    line-height: 1.5;
  }

  .parser-result {
    float: right;
    min-height: 502px;
    position: relative;
    width: 50%;
    overflow: hidden;
  }

  .json-parser {
    width: 100%;
    height: 100%;
  }

  .topright {
    position: absolute;
    right: 0;
  }
</style>
