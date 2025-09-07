<script lang="ts">
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

  let isExpansed = false;
  let isMobile = false;

  // Check if mobile on mount and window resize
  function checkMobile() {
    isMobile = window.innerWidth < 768;
    if (!isMobile) {
      isExpansed = true; // default open for laptops/tabs
    } else {
      isExpansed = false; // default closed for mobile
    }
  }

  // Initialize on mount
  if (typeof window !== 'undefined') {
    checkMobile();
    window.addEventListener('resize', checkMobile);
  }

  function toggleExpanded() {
    isExpansed = !isExpansed;
  }

  // Close sidebar when clicking on mobile nav items
  function handleMobileNavClick(callback: () => void) {
    callback();
    if (isMobile) {
      isExpansed = false;
    }
  }

  // Close sidebar when clicking overlay
  function handleOverlayClick() {
    if (isMobile && isExpansed) {
      isExpansed = false;
    }
  }
</script>


<div class="relative w-full h-full my-2 bg-red-300">
  
  <!-- Mobile Overlay -->
  {#if isMobile && isExpansed}
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <div 
      class="fixed inset-0 bg-black-200 opacity-25 z-40 transition-opacity duration-300"
      on:click={handleOverlayClick}
    ></div>
  {/if}

  <!-- Container - Grid on desktop, block on mobile -->
  <div class={`w-full h-full ${isMobile ? 'block' : 'grid grid-cols-[auto_1fr]'}`}>
    <!-- Sidebar -->
    <div class={`
      z-50 transition-transform duration-300
      ${isMobile ? 'fixed left-0 top-0 h-full' : 'relative'}
      ${isMobile && !isExpansed ? '-translate-x-full' : ''}
      ${isMobile && isExpansed ? 'translate-x-0' : ''}
    `}>
      <Navigation.Rail expanded={isExpansed}>
        {#snippet header()}
          <Navigation.Tile labelExpanded="Menu" onclick={toggleExpanded} title="Toggle Menu Width">
            <IconMenu />
          </Navigation.Tile>
        {/snippet}

        {#snippet tiles()}
          <Navigation.Tile 
            labelExpanded="Browse Files" 
            onclick={() => handleMobileNavClick(() => push('/files'))}
          >
            <IconFolder />
          </Navigation.Tile>

          <Navigation.Tile 
            labelExpanded="User Details" 
            onclick={() => handleMobileNavClick(() => push('/user'))}
          >
            <User />
          </Navigation.Tile>

          <Navigation.Tile 
            labelExpanded="Developer testimonials" 
            onclick={() => handleMobileNavClick(() => push('/testimonials'))}
          >
            <IconMusic />
          </Navigation.Tile>

          <Navigation.Tile 
            labelExpanded="Browse Videos" 
            onclick={() => handleMobileNavClick(() => push('/about'))}
          >
            <IconVideo />
          </Navigation.Tile>

          <Navigation.Tile 
            labelExpanded="Browse Games" 
            onclick={() => handleMobileNavClick(() => push('/files'))}
          >
            <IconGames />
          </Navigation.Tile>
        {/snippet}

        {#snippet footer()}
          <Navigation.Tile labelExpanded="Settings" title="Settings" onclick={() => handleMobileNavClick(() => push('/settings'))}  >
            <IconSettings />
          </Navigation.Tile>
        {/snippet}
      </Navigation.Rail>
    </div>

    <!-- Main Content -->
    <div class={`
      overflow-y-auto p-4 md:p-10 lg:p-20
      ${isMobile ? 'w-full h-full' : ''}
    `}>
      <!-- Mobile Menu Button - Only show when sidebar is closed on mobile -->
      {#if isMobile && !isExpansed}
        <button 
          class="fixed top-4 left-4 z-30 p-2 bg-gray-800 text-white rounded-md"
          on:click={toggleExpanded}
        >
          <IconMenu size={20} />
        </button>
      {/if}
      <Routes />
    </div>
  </div>
</div>

<style>
  /* Ensure smooth transitions */
  * {
    transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  }
</style>