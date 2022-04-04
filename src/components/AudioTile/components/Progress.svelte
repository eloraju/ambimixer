<script lang="ts">
  export let progress;
</script>

<div class="absolute left-0 w-[100%] self-end h-3">
  <div 
    class="h-[100%] bg-green-600 rounded-md rounded-tl-none"
    style="width: {progress}%"
    class:rounded-tr-none={progress === 100}/>
</div>