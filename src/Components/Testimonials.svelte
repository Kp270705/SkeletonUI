<script lang="ts">
  import Cards from "./Cards.svelte";
</script>

<!-- <div class="grid grid-cols-3 gap-4 p-4"> -->
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 p-4">
  <Cards classs={"card p-4 preset-filled-tertiary-500"}/>
  <Cards classs={"card p-4 preset-filled-warning-500"}/>
  <Cards classs={"card p-4 preset-filled-primary-500"}/>
  <Cards classs={"card p-4 preset-tonal-surface"}/>
<Cards classs={"card p-4 preset-filled-secondary-500"}/>
</div>