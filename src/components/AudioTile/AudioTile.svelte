<script lang="ts">
import Tag from './components/Tag.svelte';
import Progress from './components/Progress.svelte';
import ReplayButton from './components/ReplayButton.svelte';
import PlayPauseButton from './components/PlayPauseButton.svelte';
import VolumeSlider from './components/VolumeSlider.svelte';

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
	class="inline-flex align-baseline h-72 w-72 bg-zinc-400 rounded-md relative"
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
  <PlayPauseButton bind:paused={paused} playPause={playPause}/>
  <VolumeSlider bind:volume={volume} class=""/>
  <Progress progress={(playedTime/totalDur) * 100||0}/>

</div>

