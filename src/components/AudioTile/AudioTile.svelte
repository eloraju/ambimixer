
<script lang="ts">
  export let name: string;
  export let file;

  let playing = false;
  let audio = new Audio(URL.createObjectURL(file));
  audio.addEventListener('ended', ()=> {
    if(playing) {
      playing = false;
    }
  });

  async function playPause() {
    if(!playing) {
      playing = true;
      audio.play();
    } else {
      playing = false;
      audio.pause();
    }
  }

</script>

<div class="inline-grid align-baseline h-60 w-60 bg-zinc-400">
    <span class="px-4">{name}</span>
    <button class="px-2 border-black border-2 cursor-pointer"
    on:click={playPause}>{playing ? 'Pause' : 'Play'}</button>
</div>
