<script lang="ts">
  export let text = "Empty"
</script>

<div 
class="bg-green-500 absolute top-1 overflow-hidden text-ellipsis left-1 p-1 rounded-xl z-10 transition-all duration-75 delay-150 max-w-[8rem] max-h-8 hover:max-w-[75%] hover:max-h-16 hover:break-words"
>
  {text}
</div>