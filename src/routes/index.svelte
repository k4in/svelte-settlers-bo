<script lang="ts">
  type BuildOrderEntry = {
    id: string;
    building: string;
    isBuilt: boolean;
  };

  import { Trash2Icon, HammerIcon, BombIcon } from '@lucide/svelte';
  import { buildings } from '../data/buildings';
  let buildOrder = $state<BuildOrderEntry[]>([]);
</script>

<main class="grid grid-cols-2 grid-rows-[1fr] gap-10">
  <div>
    <h1>Foundation</h1>
    <ul class="flex flex-col gap-2">
      {#each buildings.foundation as building}
        <button
          class="p-2 w-full bg-neutral-200 hover:bg-neutral-300 transition-colors border-neutral-900 border rounded-sm"
          onclick={() => buildOrder.push({ id: crypto.randomUUID(), building, isBuilt: false })}
        >
          {building}
        </button>
      {/each}
    </ul>
  </div>
  <div>
    <ul class="flex flex-col gap-2">
      {#each buildOrder as entry}
        <li class={['flex items-center justify-between', entry.isBuilt && 'bg-teal-600']}>
          <span>{entry.building}</span>
          {#if entry.isBuilt}
            <div class="flex gap-1">
              <button
                class="border rounded-sm size-6 flex items-center justify-center hover:bg-neutral-200 transition-colors"
              >
                <BombIcon />
              </button>
            </div>
          {:else}
            <div class="flex gap-1">
              <button
                class="border rounded-sm size-6 flex items-center justify-center hover:bg-neutral-200 transition-colors"
                onclick={() => (entry.isBuilt = true)}
              >
                <HammerIcon class="size-4" />
              </button>
              <button
                class="border rounded-sm size-6 flex items-center justify-center hover:bg-neutral-200 transition-colors"
                onclick={() => (buildOrder = buildOrder.filter((item) => item.id !== entry.id))}
              >
                <Trash2Icon />
              </button>
            </div>
          {/if}
        </li>
      {/each}
    </ul>
  </div>
</main>
