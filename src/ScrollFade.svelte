<script>
    import { onMount } from 'svelte';
    
    let element;
    let visible = false;
  
    onMount(() => {
      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach(entry => {
            visible = entry.isIntersecting;
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