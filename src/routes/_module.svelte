<script lang="ts">
  import Header from '../components/header.svelte';
</script>

<Header />
<div class={['overflow-auto', 'p-10', 'max-h-full']}>
  <slot></slot>
</div>
