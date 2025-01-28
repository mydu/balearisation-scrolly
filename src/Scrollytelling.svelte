<script>
    import { onMount, onDestroy} from 'svelte';
    import * as d3 from 'd3';
    import Chart from './Chart.svelte';

    const sections = [
        {
            title: "dataTendency_dense",
            content:"<p>The title 'Balearisation' reflects how humans, as a geophysical force, have reshaped Mallorca through mass tourism, transforming it into one of Europe’s densest and most environmentally strained areas. Coined to describe the unchecked expansion of tourism and its adverse consequences, the term has become a widely recognised reference, originating from Mallorca and now used to critique similar phenomena globally. This transformation becomes starkly evident when comparing population densities: Mainland Spain averages 94 people per square kilometre, while Mallorca’s density surges to around 700 during peak summer tourist season.This chapter traces the anthropogenic evolution of Mallorca, highlighting the density and interconnectedness of human impacts. In 63 seconds, it spans from 1842 to today, drawing on census data that grows more detailed over time—from sporadic early records to annual updates by the 21st century. Through sonification of census and visitor data, it captures key anthropogenic events, from the first telegraph route to the carbon footprint of reverse osmosis desalination systems, providing a concise foundation for understanding human influence on the island.</p>"
        },
        { 
            title: "Data-Tendency No: 2",
            subtitle: "Disproportional",
            content:"<p>This segment highlights the stark contrast between inland towns and coastal areas of Mallorca, shaped by the rapid expansion of tourism. Coastal municipalities like Palma, Calvià, and Alcúdía experienced significant population growth and urbanisation as they became hubs for tourism infrastructure. In contrast, inland towns, particularly in Es Pla and Escorca, faced population stagnation or decline as younger generations migrated to the coast for economic opportunities.The audiovisual visualises this disparity through sonification of census and visitor data, revealing how the booming tourism industry disproportionately benefited coastal areas while leaving the interior underdeveloped. Coastal urbanisation often occurred at the expense of agricultural land, transforming Mallorca’s landscape and deepening socio-economic divides. Inland towns, once vital to Mallorca’s agricultural economy, have increasingly become marketed as tranquil retreats for affluent tourists, further exacerbating the disparity between the bustling coastline and quieter interior regions.</p>"},
        { 
            title: "Data-Tendency No: 3",
            subtitle:"Exponential",
            content:"<p>The 1950s marked a transformative tourism boom in Mallorca, fuelled by socio-economic and technological advancements in post-war Europe. Rising disposable incomes in Western Europe, particularly in the UK and Germany, combined with shorter working hours, encouraged international travel. Aviation advancements, including turbo-prop and jet engines, reduced travel times to Mallorca to just a few hours, increasing accessibility. Mallorca's own airport development, with the relocation of commercial flights to Son Sant Joan in 1959, solidified its position as a key destination. However, inconsistent data recording during the 1950s, 1960s, and 1970s limited understanding of this rapid transformation, particularly in areas such as construction, tourism, and industrial development.This gap was addressed through initiatives like the Llibre Blanc del Turisme, spearheaded by the Institut d'Estadística de les Illes Balears (IBESTAT) and supported by INESTUR. These efforts standardised and centralised data collection, offering insights into tourism-related construction, visitor numbers, and industrial impacts, enabling more informed policy-making.This segment illustrates the exponential growth in tourist arrivals, population shifts, and infrastructure development. Using sonification, it traces Mallorca’s accelerating tourism trajectory while drawing on archival records from this pivotal era.</p>"},
        { 
            title: "Data-Tendency No: 4",
            subtitle: "Undulating",
            content:"<p>The Human Pressure Indicator (HPI) was developed to provide a more accurate measurement of population load in the Balearic Islands, taking into account both residents and tourists. Unlike traditional demographic data, which often focuses solely on residents, the HPI incorporates seasonal fluctuations and resource strain caused by tourism. This comprehensive index, introduced by the Institut d'Estadística de les Illes Balears (IBESTAT), tracks daily population figures using data from airports, ports, and municipal registers.The HPI reveals striking trends, such as the seasonal surges in population during the summer months, where Mallorca’s demographic burden can exceed 1.47 million people on a single day, as recorded in August 2022. These figures underscore the significant strain on local resources, infrastructure, and ecosystems. By integrating this index, Mallorca has been able to better plan for and manage the challenges posed by fluctuating human pressure, offering a model for other tourism-dependent regions.</p>"},
        { 
            title: "Data-Tendency No: 5",
            subtitle: "Dark Figure",
            content:"<p>The prairies of Posidonia oceanica, often referred to as the “lungs of the Mediterranean,” play a critical role in producing oxygen, sequestering CO₂, and protecting coastal regions from erosion. However, these meadows face significant threats from human activities such as desalination, coastal development, and rising sea temperatures, all of which jeopardise biodiversity and the health of marine ecosystems.While research institutions such as IMEDEA provide valuable data on Posidonia meadows, these figures often carry a “dark figure,” reflecting unaccounted or underreported data. Much of this information comes from sporadic observations by volunteer scuba divers and visual surveys, often recorded in static formats like JPEG images. Despite efforts from environmental groups, city agencies, and researchers, these inconsistencies hinder a comprehensive understanding of the meadow’s condition and long-term trends.This “dark figure” highlights gaps in data coverage and limitations of current methodologies, complicating conservation efforts. To reflect the fragmented nature of the data, this segment employs an abstract, soundscape-like sonification, emphasising the urgent need for consistent and systematic monitoring.</p>"},
        { 
            title: "Data-Tendency No: 6",
            subtitle:"Deficient",
            content:"<p>Despite its abundant sunshine, Mallorca’s renewable energy investment has lagged, reaching only 25% of its electricity demand during the summer months, which is significantly behind mainland Spain. Historically, the island relied heavily on imported coal and later on oil for its energy needs, with seasonality and tourism driving sharp increases in consumption. From 1965 to 1988, electricity use skyrocketed from 496 KWh to 2,500 KWh. By 2012, a high-tension undersea cable linked the island to the mainland’s national grid, offsetting some seasonal strain but reinforcing dependency on external resources.Mallorca has begun to explore renewable options, but progress remains slow. While photovoltaic energy production has grown, it still accounts for only a fraction of the island’s energy mix. Efforts to modernise the grid and incorporate more sustainable sources have been supported by institutions such as the Institut Balear de l'Energia (IBE). Yet, the energy system reflects larger structural inefficiencies, highlighting the need for policies that prioritise sustainable, self-sufficient energy solutions for the island.</p>"},
        { 
            title: "Data-Tendency No: 7",
            subtitle:"Increasing",
            content:"<p>What we observe in the Balearic Islands, particularly in Mallorca, challenges the notion of economic growth driven by unlimited tourism, warning that in a finite world, the pursuit of perpetual growth is unsustainable. If the world consumed and emitted like Mallorca, we’d likely face a worst-case scenario with a global temperature rise of 4 to 5°C by century’s end. Delving into the feedback loops that regulate planetary and island systems uncovers a complex web of data and interactions. These systems operate at different scales and speeds, often misaligned with human temporalities. The history of the Earth system, human evolution, and industrial civilisation intertwine in unexpected ways, placing humanity in a precarious position as a geophysical force altering the planet. This segment uses data sonification and generative visuals to depict these undulating patterns and exponential risks, encouraging viewers to reflect on the urgent need for systemic changes in consumption, energy use, and policy. Mallorca’s story, though deeply local, resonates globally. It challenges us to rethink traditional metrics of success and growth, asking difficult questions about the balance between human prosperity and planetary health. The island’s struggles underscore the need for more sustainable tourism models and innovative policy interventions that respect both ecological boundaries and societal well-being.By presenting this narrative through a data-driven lens, we aim to provide a clearer understanding of the complexities and encourage actionable insights for a more balanced future. With “Balearisation” as a case study, this project invites a broader audience to reflect on how localised issues can ripple across the global stage, shaping a collective vision for coexistence in the Anthropocene.</p>"}
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
    <div class="relative w-full flex bg-[#F5F5F5]">
        <!-- Sticky sidebar -->
        <div class="w-1/3">
          <!-- {#each sections as section, i}
            <div class=" z-10 pointer-events-none"> 
                <div class="scroll-section min-h-screen flex items-center p-8" data-index={i}>
                    <div class="relative w-full p-8  flex flex-col justify-center gap-4">
                        <h2 class="text-xl font-semibold">{section.title}</h2>
                        <h1 class='text-2xl font-bold'>{section.subtitle}</h1>
                        <p>{@html section.content}</p>
                    </div>
                </div>
            </div>
          {/each} -->
            <div class=" z-10 pointer-events-none"> 
              <div class="scroll-section min-h-screen flex items-center p-8" data-index={0}>
                  <div class="relative w-full p-8  flex flex-col justify-center gap-4">
                      <h2 class="text-xl font-semibold bg-white text-[#0E23C1]">dataTendency_dense</h2>
                  </div>
              </div>
            </div>
            <div class=" z-10 pointer-events-none"> 
            <div class="scroll-section min-h-screen flex items-center p-8" data-index={1}>
                <div class="relative w-full p-8  flex flex-col justify-center gap-4">
                  <h2 class="text-xl font-semibold bg-white text-[#0E23C1]">dataTendency_disproportional</h2>

                </div>
            </div>
            </div>
            <div class=" z-10 pointer-events-none"> 
            <div class="scroll-section min-h-screen flex items-center p-8" data-index={2}>
              <div class="relative w-full p-8  flex flex-col justify-center gap-4">
                <h2 class="text-xl font-semibold bg-white text-[#0E23C1]">dataTendency_expoential</h2>

              </div>
            </div>
            </div>
            <div class=" z-10 pointer-events-none"> 
            <div class="scroll-section min-h-screen flex items-center p-8" data-index={3}>
            <div class="relative w-full p-8  flex flex-col justify-center gap-4">
              <h2 class="text-xl font-semibold bg-white text-[#0E23C1]">dataTendency_undulating</h2>

            </div>
            </div>
            </div>
            <div class=" z-10 pointer-events-none"> 
            <div class="scroll-section min-h-screen flex items-center p-8" data-index={4}>
            <div class="relative w-full p-8  flex flex-col justify-center gap-4">
              <h2 class="text-xl font-semibold bg-white text-[#0E23C1]">dataTendency_darkFigure</h2>

            </div>
            </div>
            </div>
            <div class=" z-10 pointer-events-none"> 
              <div class="scroll-section min-h-screen flex items-center p-8" data-index={5}>
                <div class="relative w-full p-8  flex flex-col justify-center gap-4">
                  <h2 class="text-xl font-semibold bg-white text-[#0E23C1]">dataTendency_deficient</h2>

                </div>
              </div>
            </div>
            <div class=" z-10 pointer-events-none"> 
              <div class="scroll-section min-h-screen flex items-center p-8" data-index={6}>
                <div class="relative w-full p-8  flex flex-col justify-center gap-4">
                  <h2 class="text-xl font-semibold bg-white text-[#0E23C1]">dataTendency_hot</h2>
                </div>
              </div>
            </div>

        </div>
        <div class="sticky top-0 right-0 h-screen w-2/3 flex items-center justify-center p-4 z-0 relative">
          {#if currentSection==3 && lineData.length>0}
            <div class="bg-black w-full h-screen">
              <Chart data={lineData} />
            </div>
            {:else}
            <div>step {currentSection}</div>
          {/if} 
        </div>
  </div>
  <svelte:window on:scroll={handleScroll} />