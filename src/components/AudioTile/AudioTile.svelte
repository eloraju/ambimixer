<script lang="ts">
	import Tag from '../Tag.svelte';
  import Fa from 'svelte-fa/src/fa.svelte';
  import {faPlay, faPause} from '@fortawesome/free-solid-svg-icons'
import Progress from './components/Progress.svelte';

	export let name: string;
	export let file;

  let audio: HTMLAudioElement;
  let volume;
  let paused = true;
  let playedTime = 0;
  let totalDur;

	function playPause() {
		if (paused) {
			audio.play();
			paused = false;
		} else {
			audio.pause();
			paused = true;
		}
	}

</script>

<div
	class="inline-grid align-baseline h-72 w-72 bg-zinc-400 rounded-md relative grid-cols-audio-tile grid-rows-audio-tile pt-5"
>
  <audio 
    bind:this={audio}
    src={URL.createObjectURL(file)}
    bind:currentTime={playedTime} 
    bind:duration={totalDur}
    bind:paused
    bind:volume
  />

	<Tag text={name} />
  <div class="flex cursor-pointer w-[100%] h-[100%]" on:click={playPause}>
    <Fa icon={paused ? faPlay : faPause} size="5x" class="m-auto"/>
  </div>  
  
  <input type="range" name="volume" min="0" max="1" step="0.001" bind:value={volume} class="h-[100%] w-[20%] justify-self-center"/>
  
  <Progress progress={(playedTime/totalDur) * 100||0} class=""/>

</div>

<style>
  input[type="range"] {
  writing-mode: bt-lr;
  -webkit-appearance: slider-vertical;
}
</style>
