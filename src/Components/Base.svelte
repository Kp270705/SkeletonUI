<script>
  import Appbar from "./Appbar.svelte";
  import Navigation from "./Navigation.svelte";
</script>

<div class="h-screen flex flex-col">
  <Appbar />
  <div class="flex flex-grow overflow-hidden">
    <Navigation />
  </div>
</div>