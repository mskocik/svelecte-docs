<script>
  import Svelecte from 'svelecte';

  let resetOnBlur = true;
  let fetchResetOnBlur = true;
  let selectionWork = null;
</script>

<Svelecte
  {resetOnBlur}
  {fetchResetOnBlur}
  bind:selection={selectionWork}
  multiple
  placeholder="Start typing ('re' for example)"
  fetch="https://jsonplaceholder.typicode.com/users/?email_like=[query]"
></Svelecte>
<div>
  <b>Selected:</b>
  <span class="float-right">
    <label for="rob" class="mr-2">
      <input type="checkbox" name="" id="rob" bind:checked={resetOnBlur}> Reset on blur
    </label>
    <label for="frob">
      <input type="checkbox" name="" id="frob" bind:checked={fetchResetOnBlur}> Reset search results on empty input
    </label>
  </span>
  <pre class="mt-1">{ JSON.stringify(selectionWork) }</pre>
</div>