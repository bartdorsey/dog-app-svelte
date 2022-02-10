<script>
  import Dog from './Dog.svelte';
  import { onMount } from "svelte"
  let dogs = []
  let selectedDogs = []
  let num = 20

  onMount(async () => {
    const response = await fetch(
      `https://dog.ceo/api/breeds/image/random/${num}`
    )
    const data = await response.json()
    dogs = data.message
  })

  const handleClick = (e) => {
    const selectedDog = e.target.src
    if (selectedDogs.includes(selectedDog)) {
      selectedDogs = selectedDogs.filter((dog) => selectedDog !== dog)
    } else {
      selectedDogs = [...selectedDogs, selectedDog]
    }
    console.log(selectedDogs)
  }
</script>

<div class="dog-list" on:click={handleClick}>
  {#each dogs as dog (dog)}
    <Dog dog={dog} isSelected={selectedDogs.includes(dog)}/>
  {/each}
</div>

<style>
  .dog-list {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
  }
</style>
