<script lang="ts">
  import Fa from 'svelte-fa';
  import {faPlay, faPause} from '@fortawesome/free-solid-svg-icons';
  export let paused: boolean = false;
  export let playPause: ()=>void;
</script>

<div class="flex cursor-pointer w-[100%] h-[100%]" on:click={playPause}>
  <Fa icon={paused ? faPlay : faPause} size="5x" class="m-auto"/>
</div>  