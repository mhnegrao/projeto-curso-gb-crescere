<script>
  export let idElement = "";
  export let label = "";
  export let valueInput = "";
  export let isInline = "false";

  function directionField(inLine) {
    console.log(inLine);
    if (inLine === "true") return "form-inline";
  }
</script>

<section>
  <div class="container">
    <div class={directionField(isInline)}>
      <div class="form-group">
        <label for={idElement}>{label}</label>
        <input
          type="text"
          bind:value={valueInput}
          id={idElement}
          class="form-control"
        />
      </div>
    </div>
  </div>
</section>

<style>
</style>
