<script>
  let payload = null;

  function onSubmit(e) {
    const object = {};
    const formData = new FormData(e.target);
    formData.forEach((value, key) => {
      if (object[key]) {
        object[key] += ', ' + value;
        return;
      }
      object[key] = value
    });
    payload = JSON.stringify(object, null, 2);
  }
</script>


<form action="" on:submit|preventDefault={onSubmit}>
  <el-svelecte
    name="parent_value" placeholder="Select parent value"
    options={`[{"value":"posts","text":"Posts"},{"value":"users","text":"Users"},{"value":"comments","text":"Comments"}]`}
    id="is-parent" required>
  </el-svelecte>
  <el-svelecte name="child_value" parent="is-parent" required placeholder="Pick from child select"
    fetch="https://jsonplaceholder.typicode.com/[parent]">
  </el-svelecte>
  <!-- server-side rendered -->
  <el-svelecte name="demo[]" options={`[{"value":"posts","text":"Posts"},{"value":"users","text":"Users"},{"value":"comments","text":"Comments"}]`} multiple
    style="margin-bottom: 0"
  >
    <select id="anchored" name="demo[]" multiple on:change={e => console.log(e.target.selectedOptions)}></select>
  </el-svelecte>
  <small>This <code>&lt;el-svelecte&gt;</code> has nested (anchored) <code>&lt;select&gt;</code>, when you need to have it rendered server-side.</small>
  <div class="mt-2">
    <button type="submit" class="btn btn-success">Send form</button>
  </div>
  {#if payload}
    <pre>{payload}</pre>
  {/if}
</form>