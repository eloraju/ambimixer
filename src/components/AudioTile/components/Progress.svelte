<script lang="ts">
  export let progress;
  let _class;
  export {_class as class}
</script>

<div class={`col-span-2 self-end h-[100%] ${_class || ''}`}>
  <div class="h-[100%] bg-green-600 rounded-md" style="width: {progress}%"/>
</div>