<script>
  import Cards from './Cards.svelte';
</script>

<div class="grid-container">
  <Cards classs="card p-4 preset-filled-tertiary-500" />
  <Cards classs="card p-4 preset-filled-warning-500" />
  <Cards classs="card p-4 preset-filled-primary-500" />
  <Cards classs="card p-4 preset-tonal-surface" />
  <Cards classs="card p-4 preset-filled-secondary-500" />
</div>

<style>
  .grid-container {
    display: grid;
    grid-template-columns: 1fr; /* default 1 col */
    gap: 1rem;
    padding: 0.5rem;
  }

  /* at ≥920px → 2 cols */
  @media (min-width: 920px) {
    .grid-container {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  /* at ≥1400px → 3 cols */
  @media (min-width: 1400px) {
    .grid-container {
      grid-template-columns: repeat(3, 1fr);
    }
  }
</style>
