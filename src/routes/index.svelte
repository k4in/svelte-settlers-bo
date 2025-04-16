<script lang="ts">
  type BuildOrderEntry = {
    building: string;
    isBuilt: boolean;
  };

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
          onclick={() => buildOrder.push({ building, isBuilt: false })}
        >
          {building}
        </button>
      {/each}
    </ul>
  </div>
  <div>
    <ul class="flex flex-col gap-2">
      {#each buildOrder as entry}
        <li class="flex items-center justify-between">
          <span class={[entry.isBuilt && 'text-teal-600']}>{entry.building}</span>
          {#if entry.isBuilt}
            <span>x</span>
          {:else}
            <button onclick={() => (entry.isBuilt = true)}>build</button>
          {/if}
        </li>
      {/each}
    </ul>
  </div>
</main>
