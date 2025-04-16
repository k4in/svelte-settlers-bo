<script lang="ts">
  type BuildOrderEntry = {
    id: string;
    building: string;
    status: 'pending' | 'isBuilt' | 'isDestroyed';
  };

  import { Trash2Icon, HammerIcon, BombIcon } from '@lucide/svelte';
  import { buildings } from '../data/buildings';
  let buildOrder = $state<BuildOrderEntry[]>([]);
</script>

<main class="grid grid-cols-2 grid-rows-[1fr] gap-10 p-6 bg-neutral-50">
  <div>
    <h1 class="text-xl font-medium mb-4 text-neutral-800">Foundation</h1>
    <ul role="list" aria-label="Available buildings" class="flex flex-col gap-3">
      {#each buildings.foundation as building}
        <button
          class="p-3 w-full bg-white hover:bg-neutral-100 active:bg-neutral-200 transition-all border-neutral-200 border rounded shadow-sm hover:shadow text-neutral-700 text-left capitalize"
          onclick={() => buildOrder.push({ id: crypto.randomUUID(), building, status: 'pending' })}
        >
          {building}
        </button>
      {/each}
    </ul>
  </div>
  <div>
    <div class="flex items-center justify-between mb-4">
      <h1 class="text-xl font-medium text-neutral-800">Build Order</h1>
      <button
        class="border rounded-md h-8 px-2 flex items-center justify-center bg-red-500 hover:bg-red-600 active:bg-red-600 text-white border-red-700 transition-colors disabled:bg-red-300 disabled:text-neutral-300 disabled:cursor-not-allowed disabled:border-red-500"
        onclick={() => (buildOrder = [])}
        disabled={buildOrder.length < 1}
        title="Reset build order"
      >
        Reset
      </button>
    </div>
    <ul class="flex flex-col gap-3" role="list" aria-label="Build Order">
      {#if buildOrder.length < 1}
        <p class="italic text-neutral-500">Click a building on the left to add it to the build order!</p>
      {:else}
        {#each buildOrder as entry}
          <li
            class={[
              'flex items-center justify-between p-3 border rounded shadow-sm transition-all',
              entry.status === 'isBuilt'
                ? 'bg-teal-500 text-white border-teal-600'
                : entry.status === 'isDestroyed'
                  ? 'bg-red-500 text-white border-red-600'
                  : 'bg-white border-neutral-200 text-neutral-700',
            ]}
          >
            <span class="capitalize">{entry.building}</span>
            {#if entry.status === 'isBuilt'}
              <div class="flex gap-1">
                <button
                  class="border rounded-md size-8 flex items-center justify-center bg-red-500 hover:bg-red-600 active:bg-red-600 text-white border-red-700 transition-colors"
                  onclick={() => (entry.status = 'isDestroyed')}
                >
                  <BombIcon class="size-4" />
                </button>
              </div>
            {:else if entry.status === 'pending'}
              <div class="flex gap-1">
                <button
                  class="border rounded-md size-8 flex items-center justify-center bg-white hover:bg-teal-50 active:bg-teal-100 text-teal-600 border-teal-200 transition-colors"
                  onclick={() => (entry.status = 'isBuilt')}
                >
                  <HammerIcon class="size-4" />
                </button>
                <button
                  class="border rounded-md size-8 flex items-center justify-center bg-white hover:bg-red-50 active:bg-red-100 text-red-600 border-red-200 transition-colors"
                  onclick={() => (buildOrder = buildOrder.filter((item) => item.id !== entry.id))}
                >
                  <Trash2Icon class="size-4" />
                </button>
              </div>
            {/if}
          </li>
        {/each}
      {/if}
    </ul>
  </div>
</main>
