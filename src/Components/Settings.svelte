<script lang="ts">
    import { Accordion } from '@skeletonlabs/skeleton-svelte';
  // Icons
  import Club from '@lucide/svelte/icons/club';
  import Diamond from '@lucide/svelte/icons/diamond';
  import Heart from '@lucide/svelte/icons/heart';
  import Spade from '@lucide/svelte/icons/spade';

  const lorem =
    'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Sit esse nisi eligendi fuga! Quas nisi repellat adipisci animi repellendus incidunt laborum sunt qui nesciunt, ducimus saepe sapiente sed ut labore. Lorem ipsum dolor, sit amet consectetur adipisicing elit. Sit esse nisi eligendi fuga! Quas nisi repellat adipisci animi repellendus incidunt laborum sunt qui nesciunt, ducimus saepe sapiente sed ut labore.';

  let value = $state(['club']);
  import { Toaster, createToaster } from '@skeletonlabs/skeleton-svelte';

  const toaster = createToaster();

   import { Popover } from '@skeletonlabs/skeleton-svelte';
  import IconX from '@lucide/svelte/icons/x';

  let openState = $state(false);

  function popoverClose() {
    openState = false;
  }
</script>

<Toaster {toaster}></Toaster>


<div class="border-8">

<Accordion {value} onValueChange={(e) => (value = e.value)}>
  <Accordion.Item value="club">
    <!-- Control -->
    {#snippet lead()}<Club size={24} />{/snippet}
    {#snippet control()}Club{/snippet}
    <!-- Panel -->
    {#snippet panel()}{lorem}{/snippet}
  </Accordion.Item>
  <hr class="hr" />
  <Accordion.Item value="diamond">
    {#snippet lead()}<Diamond size={24} />{/snippet}
    {#snippet control()}Diamond{/snippet}
    {#snippet panel()}{lorem}{/snippet}
  </Accordion.Item>
  <hr class="hr" />
  <Accordion.Item value="heart" disabled>
    {#snippet lead()}<Heart size={24} />{/snippet}
    {#snippet control()}Heart (disabled){/snippet}
    {#snippet panel()}{lorem}{/snippet}
  </Accordion.Item>
  <hr class="hr" />
  <Accordion.Item value="spade">
    {#snippet lead()}<Spade size={24} />{/snippet}
    {#snippet control()}Spade{/snippet}
    {#snippet panel()}{lorem}{/snippet}
  </Accordion.Item>
</Accordion>
</div>


<div class="toasts border-8 my-5 p-4">
    <h1 class="h1">These are toasts</h1>
    <div class=" w-full max-w-72 grid grid-cols-2 gap-2 justify-self-center ">
    <button
        class="btn preset-filled"
        onclick={() => {
        toaster.info({
            title: 'This is a toast!'
        });
        }}>Info</button
    >
    <button
        class="btn preset-filled-success-500"
        onclick={() => {
        toaster.success({
            title: 'This is a toast!'
        });
        }}>Success</button
    >
    <button
        class="btn preset-filled-warning-500"
        onclick={() => {
        toaster.warning({
            title: 'This is a toast!'
        });
        }}>Warning</button
    >
    <button
        class="btn preset-filled-error-500"
        onclick={() => {
        toaster.error({
            title: 'This is a toast!'
        });
        }}>Error</button
    >
    </div>
</div>

<div class="form border-8 my-5 p-4">
    <form class="mx-auto w-full max-w-md space-y-4">
        <input type="text" class="input" placeholder="Enter name" />
        <!-- --- -->
        <label class="label">
            <span class="label-text">Number</span>
            <input type="number" class="input" placeholder="Enter Age" />
        </label>
        <!-- --- -->
        <label class="label">
            <span class="label-text">Password</span>
            <input type="password" class="input" placeholder="Enter Password" />
        </label>
        <!-- --- -->
        <label class="label">
            <span class="label-text">Phone Number</span>
            <input type="tel" class="input" placeholder="ex: 214-555-1234" />
        </label>
        <!-- --- -->
        <label class="label">
            <span class="label-text">Search</span>
            <input type="search" class="input" placeholder="Search..." />
        </label>
    </form>
</div>



<div class=" popover my-5 border-8 p-4 ">
    <h1 class="h1">This is popover </h1>
    <div class="justify-self-center">
        <Popover
        open={openState}
        onOpenChange={(e) => (openState = e.open)}
        positioning={{ placement: 'top' }}
        triggerBase="btn preset-tonal"
        contentBase="card bg-surface-200-800 p-4 space-y-4 max-w-[320px]"
        arrow
        arrowBackground="!bg-surface-200 dark:!bg-surface-800"
        >
        {#snippet trigger()}Click Me{/snippet}
        {#snippet content()}
            <header class="flex justify-between">
            <p class="font-bold text-xl">Popover Example</p>
            <button class="btn-icon hover:preset-tonal" onclick={popoverClose} title="Close" aria-label="Close"><IconX /></button>
            </header>
            <article>
            <p class="opacity-60">
                This will display a basic popover with a header and body. This also includes a title, description, and close button.
            </p>
            </article>
        {/snippet}
        </Popover>
    </div>
</div>