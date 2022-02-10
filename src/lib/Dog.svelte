<script>
  export let dog
  export let isSelected = false;
</script>

<img class={`dog ${isSelected ? "selected" : ""}`} alt="dog" src={dog} />

<style>
  .dog {
    height: 200px;
    border-radius: 20px;
    margin: 10px;
    border: 5px solid transparent;
  }

  .dog:hover {
    cursor: pointer;
  }

  .dog.selected {
    border: 5px solid white;
  }
</style>
