<script lang="ts">
import AudioTile from './AudioTile/AudioTile.svelte';


	let files: {name: string, file: File}[] = [];
	let selectedDirectory = '';

	async function setAudioDir() {
		const handle = await window.showDirectoryPicker();
		selectedDirectory = handle.name;
		files = await listFilesInDir(handle);
		console.log(files);
	}

	async function listFilesInDir(dirHandle) {
		const files = [];
		for await (const [name, handle] of dirHandle.entries()) {
			files.push({name, file: await handle.getFile()});
		}

		return files;
	}
</script>

<div>
	<h3>Selected dir: {selectedDirectory}</h3>
	<button on:click={setAudioDir}>Select audio dir</button>
	<div class="grid grid-flow-col auto-cols-min grid-rows-auto-fill place-content-evenly bg-slate-500 gap-3 w-max">
		{#each files as file (file.name)}
			<AudioTile {...file} />
		{/each}
	</div>
</div>
