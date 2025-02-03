<script>
      import { onMount, onDestroy} from 'svelte';

  let videoElement;
  export let videoSrc = null;
  let loading = true;
  // function handleFileSelect(event) {
  //   const file = event.target.files[0];
  //   if (file) {
  //     videoSrc = URL.createObjectURL(file);
  //   }
  // }

  // function updateVideo(newSource) {
  //   if (videoSrc) {
  //     URL.revokeObjectURL(videoSrc);
  //   }
  //   videoSrc = URL.createObjectURL(newSource);
  // }

  onDestroy(() => {
    if (videoSrc) {
      URL.revokeObjectURL(videoSrc);
    }
  });
</script>

<div class="text-black w-full">
  {#if videoSrc}
    {#if loading}
      <div class="flex justify-center">loading...</div>
    {/if}
    <video 
      preload="auto"
      class="w-full {loading ? 'hidden' : ''}"
      bind:this={videoElement}
      src={videoSrc}
      controls
      on:loadeddata={()=>loading = false}
    />
  {/if}
</div>