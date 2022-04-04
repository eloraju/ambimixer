<script lang="ts">
  let _class: string = "";
  export {_class as class};
  export let volume: number = 0.5;
</script>

  <input 
  type="range" 
  min="0" 
  max="1" 
  step="0.001" 
  bind:value={volume} 
  class={`h-[90%] w-[20%] absolute right-0 top-[5%] ${_class}`}
  />


<style>
  input[type="range"] {
  writing-mode: bt-lr;
  -webkit-appearance: slider-vertical;
}
</style>