<script>
  import { onMount, createEventDispatcher } from 'svelte';
  
  const dispatch = createEventDispatcher();
  
  let element;
  let visible = false;
  let hasBeenVisible = false;

  onMount(() => {
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting && !hasBeenVisible) {
            visible = true;
            hasBeenVisible = true;
            dispatch('visible', true);
            // Once the element is visible, we can disconnect the observer
            observer.disconnect();
          }
        });
      },
      {
        threshold: 0.5
      }
    );

    observer.observe(element);

    return () => observer.disconnect();
  });
  </script>
  
  <div
    bind:this={element}
    class="transition-opacity duration-700 ease-in-out {visible ? 'opacity-100' : 'opacity-0'}"
  >
    <slot />
  </div>