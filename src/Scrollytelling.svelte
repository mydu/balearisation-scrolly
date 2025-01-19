<script>
    import { onMount, onDestroy} from 'svelte';
    import * as d3 from 'd3';
    import Chart from './Chart.svelte';

    const sections = [
        {
            title: "Data-Tendency No: 1",
            subtitle:"Dense",
            content:'<p>he title "Balearisation" reflects how humans, as a geophysical force, have reshaped Mallorca through mass tourism, transforming it into one of Europe’s densest and most environmentally strained areas. Coined to describe the unchecked expansion of tourism and its adverse consequences, the term has become a widely recognised reference, originating from Mallorca and now used to critique similar phenomena globally. This transformation becomes starkly evident when comparing population densities: Mainland Spain averages 94 people per square kilometre, while Mallorca’s density surges to around 700 during peak summer tourist season.This chapter traces the anthropogenic evolution of Mallorca, highlighting the density and interconnectedness of human impacts. In 63 seconds, it spans from 1842 to today, drawing on census data that grows more detailed over time—from sporadic early records to annual updates by the 21st century. Through sonification of census and visitor data, it captures key anthropogenic events, from the first telegraph route to the carbon footprint of reverse osmosis desalination systems, providing a concise foundation for understanding human influence on the island.</p>'
        },
        { 
            title: "Data-Tendency No: 2",
            subtitle: "Disproportional",
            content:'<p>he title "Balearisation" reflects how humans, as a geophysical force, have reshaped Mallorca through mass tourism, transforming it into one of Europe’s densest and most environmentally strained areas. Coined to describe the unchecked expansion of tourism and its adverse consequences, the term has become a widely recognised reference, originating from Mallorca and now used to critique similar phenomena globally. This transformation becomes starkly evident when comparing population densities: Mainland Spain averages 94 people per square kilometre, while Mallorca’s density surges to around 700 during peak summer tourist season.This chapter traces the anthropogenic evolution of Mallorca, highlighting the density and interconnectedness of human impacts. In 63 seconds, it spans from 1842 to today, drawing on census data that grows more detailed over time—from sporadic early records to annual updates by the 21st century. Through sonification of census and visitor data, it captures key anthropogenic events, from the first telegraph route to the carbon footprint of reverse osmosis desalination systems, providing a concise foundation for understanding human influence on the island.</p>'},
        { 
            title: "Data-Tendency No: 3",
            subtitle:"Exponential",
            content:'<p>he title "Balearisation" reflects how humans, as a geophysical force, have reshaped Mallorca through mass tourism, transforming it into one of Europe’s densest and most environmentally strained areas. Coined to describe the unchecked expansion of tourism and its adverse consequences, the term has become a widely recognised reference, originating from Mallorca and now used to critique similar phenomena globally. This transformation becomes starkly evident when comparing population densities: Mainland Spain averages 94 people per square kilometre, while Mallorca’s density surges to around 700 during peak summer tourist season.This chapter traces the anthropogenic evolution of Mallorca, highlighting the density and interconnectedness of human impacts. In 63 seconds, it spans from 1842 to today, drawing on census data that grows more detailed over time—from sporadic early records to annual updates by the 21st century. Through sonification of census and visitor data, it captures key anthropogenic events, from the first telegraph route to the carbon footprint of reverse osmosis desalination systems, providing a concise foundation for understanding human influence on the island.</p>'},
        { 
            title: "Data-Tendency No: 4",
            subtitle: "Undulating",
            content:'<p>he title "Balearisation" reflects how humans, as a geophysical force, have reshaped Mallorca through mass tourism, transforming it into one of Europe’s densest and most environmentally strained areas. Coined to describe the unchecked expansion of tourism and its adverse consequences, the term has become a widely recognised reference, originating from Mallorca and now used to critique similar phenomena globally. This transformation becomes starkly evident when comparing population densities: Mainland Spain averages 94 people per square kilometre, while Mallorca’s density surges to around 700 during peak summer tourist season.This chapter traces the anthropogenic evolution of Mallorca, highlighting the density and interconnectedness of human impacts. In 63 seconds, it spans from 1842 to today, drawing on census data that grows more detailed over time—from sporadic early records to annual updates by the 21st century. Through sonification of census and visitor data, it captures key anthropogenic events, from the first telegraph route to the carbon footprint of reverse osmosis desalination systems, providing a concise foundation for understanding human influence on the island.</p>'},
        { 
            title: "Data-Tendency No: 5",
            subtitle: "Dark Figure",
            content:'<p>he title "Balearisation" reflects how humans, as a geophysical force, have reshaped Mallorca through mass tourism, transforming it into one of Europe’s densest and most environmentally strained areas. Coined to describe the unchecked expansion of tourism and its adverse consequences, the term has become a widely recognised reference, originating from Mallorca and now used to critique similar phenomena globally. This transformation becomes starkly evident when comparing population densities: Mainland Spain averages 94 people per square kilometre, while Mallorca’s density surges to around 700 during peak summer tourist season.This chapter traces the anthropogenic evolution of Mallorca, highlighting the density and interconnectedness of human impacts. In 63 seconds, it spans from 1842 to today, drawing on census data that grows more detailed over time—from sporadic early records to annual updates by the 21st century. Through sonification of census and visitor data, it captures key anthropogenic events, from the first telegraph route to the carbon footprint of reverse osmosis desalination systems, providing a concise foundation for understanding human influence on the island.</p>'},
        { 
            title: "Data-Tendency No: 6",
            subtitle:"Deficient",
            content:'<p>he title "Balearisation" reflects how humans, as a geophysical force, have reshaped Mallorca through mass tourism, transforming it into one of Europe’s densest and most environmentally strained areas. Coined to describe the unchecked expansion of tourism and its adverse consequences, the term has become a widely recognised reference, originating from Mallorca and now used to critique similar phenomena globally. This transformation becomes starkly evident when comparing population densities: Mainland Spain averages 94 people per square kilometre, while Mallorca’s density surges to around 700 during peak summer tourist season.This chapter traces the anthropogenic evolution of Mallorca, highlighting the density and interconnectedness of human impacts. In 63 seconds, it spans from 1842 to today, drawing on census data that grows more detailed over time—from sporadic early records to annual updates by the 21st century. Through sonification of census and visitor data, it captures key anthropogenic events, from the first telegraph route to the carbon footprint of reverse osmosis desalination systems, providing a concise foundation for understanding human influence on the island.</p>'},
        { 
            title: "Data-Tendency No: 7",
            subtitle:"Increasing",
            content:'<p>he title "Balearisation" reflects how humans, as a geophysical force, have reshaped Mallorca through mass tourism, transforming it into one of Europe’s densest and most environmentally strained areas. Coined to describe the unchecked expansion of tourism and its adverse consequences, the term has become a widely recognised reference, originating from Mallorca and now used to critique similar phenomena globally. This transformation becomes starkly evident when comparing population densities: Mainland Spain averages 94 people per square kilometre, while Mallorca’s density surges to around 700 during peak summer tourist season.This chapter traces the anthropogenic evolution of Mallorca, highlighting the density and interconnectedness of human impacts. In 63 seconds, it spans from 1842 to today, drawing on census data that grows more detailed over time—from sporadic early records to annual updates by the 21st century. Through sonification of census and visitor data, it captures key anthropogenic events, from the first telegraph route to the carbon footprint of reverse osmosis desalination systems, providing a concise foundation for understanding human influence on the island.</p>'}
    ];
  
    let currentSection = 0;

  function setupIntersectionObserver() {
    const options = {
      root: null,
      rootMargin: '0px',
      threshold: 0.5
    };
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          const index = parseInt(entry.target.getAttribute('data-index') || '0');
          currentSection = index;
        }
      });
    }, options);
    document.querySelectorAll('.scroll-section').forEach(section => {
      observer.observe(section);
    });
  }
    let tooltipX=0;
    let tooltipY=0;
    let isTooltip=false;
    let activeTooltip = null;
    let clientWidth;
    let clientHeight;
    
    // const showTooltip = (e,index) => {
    //   console.log(e,index)
    //   isTooltip=true;
    //   tooltipX=e.clientX+200<clientWidth ? e.clientX+20: e.clientX-200; 
    //   tooltipY= e.clientY+10<clientHeight ? e.clientY+10 : e.clientY-100;
    //   activeTooltip = tooltips[index]
    // }
    const handleScroll = () => {
      isTooltip=false;
      activeTooltip = null;
    };
    // onMount(() => {
    //   setupIntersectionObserver();
    //   // window.addEventListener('scroll', handleScroll);
    // });
    let lineData = [];

onMount(async () => {
  setupIntersectionObserver();
    try {
      const raw = await d3.csv('data/iph.csv', d3.autoType);
      const parseDate = d3.timeParse("%m/%Y");
      lineData = raw.filter(d => ('' + d.month).length !== 4).map(d => ({ ...d, date: parseDate(d.month) })).sort((a,b)=>a.date-b.date);
    } catch (error) {
        console.error('Error loading CSV file:', error);
    }
});
    // onDestroy(() => {
    //   window.removeEventListener('scroll', handleScroll);
    // });
  </script>
    <div class="relative w-full flex bg-[#ccc]">
        <!-- Sticky sidebar -->
        <div class="w-1/3">
            {#each sections as section, i}
            <div class=" z-10 pointer-events-none"> 
                <div class="scroll-section min-h-screen flex items-center p-8" data-index={i}>
                    <div class="relative w-full p-8  flex flex-col justify-center gap-4">
                        <h2 class="text-xl font-semibold">{section.title}</h2>
                        <h1 class='text-2xl font-bold'>{section.subtitle}</h1>
                        <p>{@html section.content}</p>
                    </div>
                </div>
            </div>
        {/each}
        </div>
        <div class="sticky top-0 right-0 h-screen w-2/3 flex items-center justify-center p-4 z-0 bg-black">
          {#if currentSection==3 && lineData.length>0}
            <Chart data={lineData} />
          {/if}
        </div>
  </div>
  <svelte:window on:scroll={handleScroll} />