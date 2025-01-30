<script>
    import { onMount, onDestroy} from 'svelte';
    import * as d3 from 'd3';
    import Chart from './Chart.svelte';
    import ScrollFade from './ScrollFade.svelte';

    const steps = [
        {
            title: "dataTendency_dense",
            subsections: [
              {
                subtitle:'_origin',delay:0.2,
                color:"#0E23C1",
                icon: 'assets/title_origin.svg',
                content:'<p>The title "Balearisation" reflects how humans, as a geophysical force, have reshaped Mallorca through mass tourism, transforming it into one of Europe’s densest and most environmentally strained areas. Coined to describe the unchecked expansion of tourism and its adverse consequences, the term has become a widely recognised reference, originating from Mallorca and now used to critique similar phenomena globally. </p>'
              },
              {
                subtitle:'_issue',delay:0.3,
                color:"#B40A47",
                icon: 'assets/title_issue.svg',
                content:'<p>The title "Balearisation" reflects how humans, as a geophysical force, have reshaped Mallorca through mass tourism, transforming it into one of Europe’s densest and most environmentally strained areas. Coined to describe the unchecked expansion of tourism and its adverse consequences, the term has become a widely recognised reference, originating from Mallorca and now used to critique similar phenomena globally. </p>'
              },
              {
                subtitle:'_sonification approach',delay:0.5,
                color:"#000000",
                icon: 'assets/title_sonification.svg',
                content:'<p>This chapter traces the anthropogenic evolution of Mallorca, highlighting the density and interconnectedness of human impacts. In 63 seconds, it spans from 1842 to today, drawing on census data that grows more detailed over time—from sporadic early records to annual updates by the 21st century. Through sonification of census and visitor data, it captures key anthropogenic events, from the first telegraph route to the carbon footprint of reverse osmosis desalination systems, providing a concise foundation for understanding human influence on the island.</p>'
              },
              {
                subtitle:'notification',
                delay: 0.6,
                content:"Pushing play or scrolling will trigger the next audiovisual segment, immersing viewers in these dynamics."
              }
            ]
        },
        { 
            title: "dataTendency_disproportional",
            subsections: [
              {
                subtitle:'_origin',delay:0.2,
                color:"#0E23C1",
                icon: 'assets/title_origin.svg',
                content:'<p>This segment highlights the stark contrast between inland towns and coastal areas of Mallorca, shaped by the rapid expansion of tourism. </p>'
              },
              {
                subtitle:'_issue',delay:0.3,
                color:"#B40A47",
                icon: 'assets/title_issue.svg',
                content:'<p>Coastal municipalities like Palma, Calvià, and Alcúdía experienced significant population growth and urbanisation as they became hubs for tourism infrastructure. In contrast, inland towns, particularly in Es Pla and Escorca, faced population stagnation or decline as younger generations migrated to the coast for economic opportunities.</p>'
              },
              {
                subtitle:'_sonification approach',delay:0.5,
                color:"#000000",
                icon: 'assets/title_sonification.svg',
                content:'<p>The audiovisual visualises this disparity through sonification of census and visitor data, revealing how the booming tourism industry disproportionately benefited coastal areas while leaving the interior underdeveloped. Coastal urbanisation often occurred at the expense of agricultural land, transforming Mallorca’s landscape and deepening socio-economic divides. Inland towns, once vital to Mallorca’s agricultural economy, have increasingly become marketed as tranquil retreats for affluent tourists, further exacerbating the disparity between the bustling coastline and quieter interior regions.</p>'
              },
              {
                subtitle:'notification',
                delay: 0.6,
                content:"Pushing play or scrolling will trigger the next audiovisual segment, immersing viewers in these dynamics."
              }
            ]
          },
        { 
            title: "dataTendency_expoential",
            subsections: [
              {
                subtitle:'_origin',delay:0.2,
                color:"#0E23C1",
                icon: 'assets/title_origin.svg',
                content: "<p>The 1950s marked a transformative tourism boom in Mallorca, driven by socio-economic recovery and technological advancements in post-war Europe. With rising disposable incomes and reduced working hours in countries like the UK and Germany, international travel became more accessible. Innovations in aviation, such as turbo-prop and jet engines, drastically cut travel times, and the relocation of commercial flights to Son Sant Joan in 1959 solidified Mallorca's status as a key destination.</p>"
              },
              {
                subtitle:'_issue',delay:0.3,
                color:"#B40A47",
                icon: 'assets/title_issue.svg',
                content:'  <p>Despite the boom, inconsistent data recording during the 1950s, 1960s, and 1970s limited the ability to fully grasp the transformation’s impact. Critical areas like construction, tourism, and industrial development lacked cohesive documentation, making informed policy-making difficult.</p>'
              },
              {
                subtitle:'_insight',delay:0.4,
                color:"#12A331",
                icon: 'assets/title_insight.svg',
                content:'<p>This gap was addressed by initiatives such as the Llibre Blanc del Turisme, led by IBESTAT and INESTUR, which centralised and standardised data collection. These efforts provided valuable insights into infrastructure development and the rapid growth of tourist arrivals.</p>'
              },
              {
                subtitle:'_sonification & visualisation approach',delay:0.5,
                color:"#000000",
                icon: 'assets/title_sonification.svg',
                content:"<p>This segment employs sonification to represent Mallorca's accelerating tourism trajectory and its broader infrastructural development. The audiovisual draws on datasets covering the surface area of approved projects across residential, tourism, industrial, and recreational sectors from 1987 to 2024.</p><p>A monophonic oscillator represents the aggregated data for these sectors, with pitch increasing steadily over time to signify exponential growth. Accompanying visuals, derived from generative shaders and abstract imagery, contextualise these trends, linking historical development to auditory and visual elements.</p>"
              },
              {
                subtitle:'notification',
                delay: 0.6,
                content:"By interacting with the media player, viewers can explore how growth across these sectors shaped Mallorca’s transformation during this pivotal era."
              }
            ]
          },
        { 
            title: "dataTendency_undulating",
            subsections: [
              {
                subtitle:'_origin',delay:0.2,
                color:"#0E23C1",
                icon: 'assets/title_origin.svg',
                content: " <p>The Human Pressure Indicator (HPI) was developed to provide a more accurate measurement of population load in the Balearic Islands, accounting for both residents and tourists. Traditional demographic data often focused solely on residents, but the HPI incorporates seasonal fluctuations and resource strain caused by tourism. This index, introduced by the Institut d'Estadística de les Illes Balears (IBESTAT), uses data from airports, ports, and municipal registers to track daily population figures.</p>"
              },
              {
                subtitle:'_issue',delay:0.3,
                color:"#B40A47",
                icon: 'assets/title_issue.svg',
                content: "<p>The HPI reveals striking trends, such as seasonal surges during summer, when Mallorca’s population burden can exceed 1.47 million people on a single day (e.g., August 2022). These figures highlight the strain on local resources, infrastructure, and ecosystems, which require advanced planning and adaptive management.</p>"
              },
              {
                subtitle:'_insight',delay:0.4,
                color:"#12A331",
                icon: 'assets/title_insights.svg',
                content:'<p>By integrating the HPI, Mallorca has improved its ability to plan and manage the challenges posed by fluctuating human pressure. The index serves as a model for other tourism-dependent regions grappling with similar issues.</p>'
              },
              {
                subtitle:'_sonification & visualisation approach',delay:0.5,
                color:"#000000",
                icon: 'assets/title_sonification.svg',
                content:"<p>This interactive approach immerses viewers in the dynamics of the HPI, providing a deeper understanding of its implications. The sonification employs pitch to clearly illustrate the fluctuations between high (summer) seasons and low (winter) seasons, capturing the seasonal variability of human pressure on the island.</p>"
              },
              {
                subtitle:'notification',
                delay: 0.6,
                content:"Pushing play or scrolling will trigger the next data visualisation and sonification, including an interactive visualisation of the HPI."
              }
            ]
          },
        { 
            title: "dataTendency_darkFigure",
            subsections: [
              {
                subtitle:'_origin',delay:0.2,
                color:"#0E23C1",
                icon: 'assets/title_origin.svg',
                content: "  <p>The prairies of Posidonia oceanica, often called the “lungs of the Mediterranean,” play a crucial ecological role in oxygen production, CO₂ sequestration, and coastal protection. However, they face growing threats from human activities, including desalination, coastal development, and rising sea temperatures, which jeopardise biodiversity and the health of marine ecosystems.</p>"
              },
              {
                subtitle:'_issue',delay:0.3,
                color:"#B40A47",
                icon: 'assets/title_issue.svg',
                content: "<p>While research institutions such as IMEDEA provide valuable data on Posidonia meadows, the information often carries a “dark figure” — unaccounted or underreported data. Much of the available information relies on sporadic volunteer scuba divers’ observations and visual surveys, often recorded in static formats like JPEG images. These inconsistencies hinder a comprehensive understanding of the meadows' condition and their long-term trends.</p>"
              },
              {
                subtitle:'_insight',delay:0.4,
                color:"#12A331",
                icon: 'assets/title_insights.svg',
                content:'  <p>The “dark figure” underscores the gaps in data coverage and limitations of existing methodologies, complicating conservation efforts. It highlights the urgent need for systematic and consistent monitoring to better assess the health and sustainability of these ecosystems.</p>'
              },
              {
                subtitle:'_sonification & visualisation approach',delay:0.5,
                color:"#000000",
                icon: 'assets/title_sonification.svg',
                content:"<p>This segment employs a soundscape-like sonification to reflect the fragmented nature of the data. By using pan, the sonification differentiates between healthy organisms (heard from the left channel) and morbid or stressed ones (heard from the right channel). This immersive auditory experience highlights the disparities in the ecosystem while emphasising the need for systematic data collection and conservation efforts.</p>"
              },
              {
                subtitle:'notification',
                delay: 0.6,
                content:"Pushing play or scrolling will trigger the next audiovisual segment, allowing viewers to explore the dynamics of Posidonia oceanica through sonification and abstract visualisation."
              }
            ]
          },
        { 
            title: "dataTendency_deficient",
            subsections: [
              {
                subtitle:'_origin',delay:0.2,
                color:"#0E23C1",
                icon: 'assets/title_origin.svg',
                content: "  <p>Despite Mallorca’s abundant sunshine, its renewable energy investment has lagged behind, with renewable sources meeting only 25% of electricity demand during the summer months—far below mainland Spain. Historically, the island depended on imported coal and oil for energy, with seasonality and tourism driving sharp consumption increases. Between 1965 and 1988, electricity use rose dramatically from 496 KWh to 2,500 KWh. The introduction of a high-tension undersea cable in 2012 connected the island to the mainland’s national grid, alleviating some seasonal strain but deepening reliance on external resources.</p>"
              },
              {
                subtitle:'_issue',delay:0.3,
                color:"#B40A47",
                icon: 'assets/title_issue.svg',
                content: "<p>Renewable energy adoption remains sluggish despite some progress in photovoltaic energy production. The renewable sector still accounts for only a fraction of Mallorca’s energy mix. Efforts to modernise the grid and incorporate sustainable sources have been made by institutions like the Institut Balear de l'Energia (IBE), but structural inefficiencies persist. This underscores the urgent need for policies that prioritise sustainable, self-sufficient energy solutions tailored to the island’s unique conditions.</p>"
              },
              {
                subtitle:'_insight',delay:0.4,
                color:"#12A331",
                icon: 'assets/title_insights.svg',
                content:'<p>The stark contrast between fossil fuel dependency and renewable energy adoption highlights systemic inefficiencies in the energy infrastructure. These disparities serve as a case study for other regions grappling with similar challenges, emphasising the importance of proactive investment in sustainability.</p>'
              },
              {
                subtitle:'_sonification & visualisation approach',delay:0.5,
                color:"#000000",
                icon: 'assets/title_sonification.svg',
                content:" <p>The sonification juxtaposes fossil fuel and renewable energy data, using pitch and dynamics to illustrate their contrasting trends over time. The left and right channels reflect the respective contributions of each energy source, enabling listeners to perceive the imbalance and the slow progress toward sustainability.</p>"
              },
              {
                subtitle:'notification',
                delay: 0.6,
                content:"The media player provides an interactive experience where users can isolate the data: fossil fuel consumption is represented in the left audio channel, while renewable energy data plays on the right. Combined playback delivers a complete auditory representation of the energy dynamics."
              }
            ]
          },
        { 
            title: "dataTendency_hot",
            subsections: [
              {
                subtitle:'_origin',delay:0.2,
                color:"#0E23C1",
                icon: 'assets/title_origin.svg',
                content: "  <p>What we observe in the Balearic Islands, particularly in Mallorca, challenges the notion of economic growth driven by unlimited tourism. In a finite world, the pursuit of perpetual growth is unsustainable. If global consumption and emissions matched Mallorca’s levels, we’d likely face a worst-case scenario.</p>"
              },
              {
                subtitle:'_issue',delay:0.3,
                color:"#B40A47",
                icon: 'assets/title_issue.svg',
                content: "<p>The feedback loops regulating planetary and island systems reveal a complex web of data and interactions. These systems often operate at mismatched scales and speeds compared to human activities, complicating efforts to align short-term actions with long-term planetary stability. The intertwined histories of the Earth system, human evolution, and industrial civilisation place humanity in a precarious position as a geophysical force with unprecedented planetary impacts.</p>"
              },
              {
                subtitle:'_insight',delay:0.4,
                color:"#12A331",
                icon: 'assets/title_insights.svg',
                content:' <p>This segment explores the undulating patterns and exponential risks associated with unchecked consumption, energy use, and policy inertia. By using Mallorca as a case study, it highlights the urgent need for systemic changes in economic and environmental practices, not just locally but globally.</p>'
              },
              {
                subtitle:'_sonification & visualisation approach',
                delay:0.5,
                color:"#000000",
                icon: 'assets/title_sonification.svg',
                content:"   <p>The sonification reflects the contrasting scales and patterns of human activity versus planetary systems. Generative visuals accompany the sonification, illustrating the interconnected risks of consumption, energy use, and global temperature rise. The immersive combination encourages reflection on the need for transformative policy and individual action.</p>"
              },
              {
                subtitle:'notification',
                delay: 0.6,
                content:"Pushing play or scrolling triggers the audiovisual segment, using data sonification and generative visuals to immerse viewers in these dynamics."
              }
            ]
          },
    ];
    let sections =[];
    let currentSection = 0;
    let stepProgress = new Array(steps.length).fill(0);
    
    // function setupIntersectionObserver() {
  //   const options = {
  //     root: null,
  //     rootMargin: '0px',
  //     threshold: 0.5
  //   };
  //   const observer = new IntersectionObserver((entries) => {
  //     entries.forEach(entry => {
  //       if (entry.isIntersecting) {
  //         const index = parseInt(entry.target.getAttribute('data-index') || '0');
  //         currentSection = index;
  //       }
  //     });
  //   }, options);
  //   document.querySelectorAll('.scroll-section').forEach(section => {
  //     observer.observe(section);
  //   });
  // }


    let clientWidth;
    let clientHeight;

    function calculateScrollProgress(element) {
      const rect = element.getBoundingClientRect();
      const windowHeight = window.innerHeight;
      const elementHeight = rect.height;
        // If element is completely below viewport
        if (rect.top >= windowHeight) {
          return 0;
        }
        
        // If element is completely above viewport
        if (rect.bottom <= 0) {
          return 1;
        }
        
        // Calculate how much has been scrolled through
        const distanceFromTop = elementHeight - rect.top;
        const totalDistance = elementHeight + windowHeight;
        const progress = distanceFromTop / totalDistance;
        
        return Math.min(1, Math.max(0, progress));
      }

    const handleScroll = () => {
        sections.forEach((section, index) => {
        stepProgress[index] = calculateScrollProgress(section);
      });
      stepProgress = [...stepProgress]; // Trigger reactivity
    };

    let lineData = [];
    let observer;
    onMount(async () => {
      // setupIntersectionObserver();
        try {
          const raw = await d3.csv('data/iph.csv', d3.autoType);
          const parseDate = d3.timeParse("%m/%Y");
          lineData = raw.filter(d => ('' + d.month).length !== 4).map(d => ({ ...d, date: parseDate(d.month) })).sort((a,b)=>a.date-b.date);
        } catch (error) {
            console.error('Error loading CSV file:', error);
        }

        observer = new IntersectionObserver(
            (entries) => {
              entries.forEach((entry) => {
                if (entry.isIntersecting) {
                  const index = sections.indexOf(entry.target);
                  if (index !== -1) {
                    currentSection = index;
                  }
                }
              });
            },
            {
              root: null,
              threshold: 0.5,
            }
          );

          sections.forEach((section) => {
            observer.observe(section);
          });

          // window.addEventListener('scroll', handleScroll);
          handleScroll(); // Initial calculation

          return () => {
            observer.disconnect();
            window.removeEventListener('scroll', handleScroll);
          };
    
    });
    // onDestroy(() => {
    //   window.removeEventListener('scroll', handleScroll);
    // });
  </script>
    <div class="relative w-full lg:flex bg-[#EEF1F4]">
        <!-- Sticky sidebar -->
        <div class="w-full lg:w-1/3">
          {#each steps as section, i}
              <div class="scroll-section min-h-screen flex p-8 relative" bind:this={sections[i]} data-index={i}>
                  <div class="relative w-full py-16 px-8 flex flex-col gap-8 justify-center">
                    <div class="flex justify-between items-end">
                      <h2 class="text-xl font-semibold text-[#0E23C1]"><span class="bg-white px-2">{steps[i].title}</span></h2>
                      <img src="assets/map{i}.svg" class="w-[200px]">

                    </div>
                      {#each steps[i].subsections as subsection}
                      <ScrollFade>
                        <div class="flex gap-2" style="color:{subsection.color}">

                          {#if subsection.subtitle!=='notification'}
                            <img class="w-4 h-4 mt-2" src={subsection.icon} />
                            <div>
                                <h3 class="text-lg font-semibold">{subsection.subtitle}</h3>
                                {@html subsection.content}
                              </div>
                          <!-- {:else}
                            <div class="rounded-xl bg-white px-6 py-2">{subsection.content}</div> -->
                          {/if}
                        </div>
                      </ScrollFade>
                      {/each}
                      <ScrollFade>
                        <div class="block lg:hidden">
                          {#if i==3 && lineData.length>0}
                            <div class="bg-black w-full h-[50vh] lg:h-screen">
                              <Chart data={lineData} />
                            </div>
                            {:else}
                            <div class="bg-black text-white w-full h-[50vh]"></div>
                          {/if} 
                        </div>
                      </ScrollFade>
                  </div>
              </div>
              <!-- <div class="h-[50vh]"></div> -->
          {/each}

        </div>
        <div class="hidden lg:block sticky top-0 left:0 h-screen w-full lg:w-2/3 flex items-center justify-center p-4 z-0 relative">
          {#if currentSection==3 && lineData.length>0}
            <div class="bg-black w-full h-screen">
              <Chart data={lineData} />
            </div>
            {:else}
            <div class="bg-black text-white w-full h-full"></div>
          {/if} 
        </div>
  </div>
  <svelte:window on:scroll={handleScroll} />