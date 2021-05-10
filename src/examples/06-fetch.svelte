<script>
  import Svelecte from 'svelecte';

  let resetOnBlur = true;
  let fetchResetOnBlur = true;
</script>

<Svelecte
  {resetOnBlur}
  {fetchResetOnBlur}
  multiple
  placeholder="Start typing ('re' for example)"
  fetch="https://my-json-server.typicode.com/mskocik/svelecte-docs/colors?value_like=[query]"
></Svelecte>
<div class="text-right">
  <label for="rob" class="mr-2">
    <input type="checkbox" name="" id="rob" bind:checked={resetOnBlur}> Reset on blur
  </label>
  <label for="frob">
    <input type="checkbox" name="" id="frob" bind:checked={fetchResetOnBlur}> Reset search results on empty input
  </label>
</div>