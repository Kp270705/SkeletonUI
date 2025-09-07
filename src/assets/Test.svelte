<!-- Testimonials.svelte: 

<script lang="ts">
  import Cards from "./Cards.svelte";
</script>

<h1 class="h1 my-3.5">This is Testimonials page: </h1>
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 px-4 md:px-10 lg:px-20">
  
  <Cards classs={"card p-4 preset-filled-tertiary-500"}/>
  <Cards classs={"card p-4 preset-filled-warning-500"}/>
  <Cards classs={"card p-4 preset-filled-primary-500"}/>
  <Cards classs={"card p-4 preset-tonal-surface"}/>
  <Cards classs={"card p-4 preset-filled-secondary-500"}/>

</div> -->


<!-- =================================================== -->


<!-- Navigation.svelte:  -->



<!-- <script lang="ts">
  import { Navigation } from '@skeletonlabs/skeleton-svelte';
  import IconMenu from '@lucide/svelte/icons/menu';
  import IconFolder from '@lucide/svelte/icons/folder';
  import IconMusic from '@lucide/svelte/icons/music';
  import IconVideo from '@lucide/svelte/icons/video';
  import IconGames from '@lucide/svelte/icons/gamepad';
  import IconSettings from '@lucide/svelte/icons/settings';
  import User from '@lucide/svelte/icons/user-round';
  import { push } from 'svelte-spa-router';
  import Routes from "./routes/Routes.svelte";

  // let isExpansed = $state(false);
  let isExpansed = false;

  $: (() => {
		if (window.innerWidth >= 768) {
			isExpansed = true; // default open for laptops/tabs
		}
	});

  function toggleExpanded() {
    isExpansed = !isExpansed;
  }
</script>


<div class="border-t-1 grid grid-cols-[auto_1fr] w-full h-full bg-green-200">
  <Navigation.Rail expanded={isExpansed}>
    {#snippet header()}
      <Navigation.Tile labelExpanded="Menu" onclick={toggleExpanded} title="Toggle Menu Width"><IconMenu /></Navigation.Tile>
    {/snippet}
    {#snippet tiles()}
      <Navigation.Tile labelExpanded="Browse Files" onclick={ ()=> { push('/files') }}>
        <IconFolder />
      </Navigation.Tile>
      <Navigation.Tile labelExpanded="User Details" onclick={ ()=> { push('/user') }}>
        <User />
      </Navigation.Tile>
      <Navigation.Tile labelExpanded="Developer testimonials" onclick={ ()=> { push('/testimonials') }}>
        <IconMusic />
      </Navigation.Tile>
      <Navigation.Tile labelExpanded="Browse Videos" onclick={ ()=> { push('/about') }}>
        <IconVideo />
      </Navigation.Tile>
      <Navigation.Tile labelExpanded="Browse Games" onclick={ ()=> { push('/files') }}>
        <IconGames />
      </Navigation.Tile>
    {/snippet}
    {#snippet footer()}
      <Navigation.Tile labelExpanded="Settings" href="/settings" title="Settings"><IconSettings /></Navigation.Tile>
    {/snippet}
  </Navigation.Rail>

  <div class="overflow-y-auto p-4 md:p-10 lg:p-20 bg-red-300">
    <Routes />
  </div>

</div> -->


