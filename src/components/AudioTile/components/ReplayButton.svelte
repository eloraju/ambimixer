<script lang="ts">
  import Fa from 'svelte-fa';
  import {faRepeat} from '@fortawesome/free-solid-svg-icons';
  export let repeating = false;
</script>

<div>
    {#if repeating}
    <Fa icon={faRepeat}/>
    {:else}
    <Fa icon={faRepeat}/>
    {/if}
</div>