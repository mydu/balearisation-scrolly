<script>
    import { onMount, onDestroy} from 'svelte';
    import * as d3 from 'd3';
    import Chart from './Chart.svelte';
    import ScrollFade from './ScrollFade.svelte';
    import { tweened } from 'svelte/motion';
    import { linear } from 'svelte/easing';
    import Video from './Video.svelte';

    const steps = [
        {
            title: "dataTendency_dense",
            video:"https://burakkorkmaz.de/content/files/01_Intro.mp4",
            youtube:"https://www.youtube.com/embed/udCt5PE9g6k",
            background:"#EEF1F4",
            mapInfo:   {
              "location": "Mallorca (all municipalities)",
              "yearRange": "1886-2023",
              "source": [
               { 
                url: "https://www.ine.es/",
                title:"INE"

               },
               { 
                url: "https://ibestat.es/?lang=ca",
                title:"IBESTAT"
               },
                
              ]
            },
            subsections: [
              {
                subtitle:'_origin',delay:0.2,
                color:"#0E23C1",
                icon: 'assets/title_origin.svg',
                content:'<p>The title "<strong>Balearisation</strong>" reflects how humans, as a geophysical force, have reshaped Mallorca through mass tourism, transforming it into one of Europe’s densest and most environmentally strained areas. Coined to describe the unchecked expansion of tourism and its adverse consequences, the term has become a widely recognised reference, originating from Mallorca and now used to critique similar phenomena globally. </p>'
              },
              {
                subtitle:'_issue',delay:0.3,
                color:"#B40A47",
                icon: 'assets/title_issue.svg',
                content:'<p>This transformation becomes starkly evident when comparing population densities: <strong>Mainland Spain averages 94 people per square kilometre, while Mallorca’s density surges to around 700 during peak summer tourist season.</strong></p>'
              },
              {
                subtitle:'_sonification approach',
                delay:0.5,
                color:"#000000",
                icon: 'assets/title_sonification.svg',
                content:'<p>This chapter traces the anthropogenic evolution of Mallorca, highlighting the density and interconnectedness of human impacts. <strong>In 63 seconds, it spans from 1842 to today, drawing on census data that grows more detailed over time—from sporadic early records to annual updates by the 21st century.</strong> Through sonification of census and visitor data, it captures key anthropogenic events, from the first telegraph route to the carbon footprint of reverse osmosis desalination systems, providing a concise foundation for understanding human influence on the island.</p>'
              },
              {
                subtitle:'notification',
                delay: 0.6,
                content:"Simply pressing play will trigger the next audiovisual segment, immersing viewers in these dynamics."
              }
            ]
        },
        { 
            title: "dataTendency_disproportional",
            video:"https://burakkorkmaz.de/content/files/02_Denso.mp4",
            youtube:"https://www.youtube.com/embed/v-Oabz0GyuE",
            background:"#E0E4E9",
            mapInfo:  
              {
                "location": ["Palma", "Calvià", "Alcúdía", "Escorca"],
                "yearRange": "1920-2024",
                "source": [
               { 
                url: "https://www.ine.es/",
                title:"INE"

               },
               { 
                url: "https://ibestat.es/?lang=ca",
                title:"IBESTAT"
               },
                
              ]
              },
            subsections: [
              {
                subtitle:'_origin',delay:0.2,
                color:"#0E23C1",
                icon: 'assets/title_origin.svg',
                content:'<p>This segment highlights <strong>the stark contrast between inland towns and coastal areas of Mallorca, shaped by the rapid expansion of tourism.</strong></p>'
              },
              {
                subtitle:'_issue',delay:0.3,
                color:"#B40A47",
                icon: 'assets/title_issue.svg',
                content:'<p>Coastal municipalities like <strong>Palma</strong>, <strong>Calvià</strong>, and <strong>Alcúdía</strong> experienced significant population growth and urbanisation as they became hubs for tourism infrastructure. In contrast, inland towns, particularly in <strong>Es Pla</strong> and <strong>Escorca</strong>, faced population stagnation or decline as younger generations migrated to the coast for economic opportunities.</p>'
              },
              {
                subtitle:'_sonification approach',delay:0.5,
                color:"#000000",
                icon: 'assets/title_sonification.svg',
                content:'<p>The audiovisual visualises this disparity through sonification of census and visitor data, revealing <strong>how the booming tourism industry disproportionately benefited coastal areas while leaving the interior underdeveloped.</strong> Coastal urbanisation often occurred at the expense of agricultural land, transforming Mallorca’s landscape and deepening socio-economic divides. Inland towns, once vital to Mallorca’s agricultural economy, have increasingly become marketed as tranquil retreats for affluent tourists, further exacerbating the disparity between the bustling coastline and quieter interior regions.</p>'
              },
              {
                subtitle:'notification',
                delay: 0.6,
                content:"Simply pressing play will trigger the next audiovisual segment, immersing viewers in these dynamics.."
              }
            ]
          },
        { 
            title: "dataTendency_exponential",
            video:"https://burakkorkmaz.de/content/files/03_Ocio_Construction.mp4",
            youtube:"https://www.youtube.com/embed/jfvdsAhRpJ4",
            background:"#EEF1F4",
            mapInfo:  
              {
              "location": "Mallorca (all municipalities)",
              "yearRange": " 1987-2024, mensual",
              "source": [
               { 
                url: "https://www.ine.es/",
                title:"INE"

               },
               { 
                url: "https://ibestat.es/?lang=ca",
                title:"IBESTAT"
               },
                
              ]
            },
            subsections: [
              {
                subtitle:'_origin',delay:0.2,
                color:"#0E23C1",
                icon: 'assets/title_origin.svg',
                content: "<p><strong>The 1950s marked a transformative tourism boom in Mallorca</strong>, driven by socio-economic recovery and technological advancements in post-war Europe. With rising disposable incomes and reduced working hours in countries like the UK and Germany, international travel became more accessible. Innovations in aviation, such as turbo-prop and jet engines, drastically cut travel times, and <strong>the relocation of commercial flights to Son Sant Joan in 1959 solidified Mallorca's status as a key destination.</strong></p>"
              },
              {
                subtitle:'_issue',delay:0.3,
                color:"#B40A47",
                icon: 'assets/title_issue.svg',
                content:'  <p>Despite the boom, inconsistent data recording during the 1950s, 1960s, and 1970s limited the ability to fully grasp the transformation’s impact. <strong>Critical areas like construction, tourism, and industrial development lacked cohesive documentation, making informed policy-making difficult.</strong></p>'
              },
              {
                subtitle:'_insight',delay:0.4,
                color:"#12A331",
                icon: 'assets/title_insights.svg',
                content:'<p>This gap was addressed by initiatives such as the Llibre Blanc del Turisme, led by IBESTAT and INESTUR, which centralised and standardised data collection. These efforts provided valuable insights into infrastructure development and the rapid growth of tourist arrivals.</p>'
              },
              {
                subtitle:'_sonification & visualisation approach',delay:0.5,
                color:"#000000",
                icon: 'assets/title_sonification.svg',
                content:"<p>This segment employs sonification to represent Mallorca's accelerating tourism trajectory and its broader infrastructural development. <strong>The audiovisual draws on datasets covering the surface area of approved projects across residential, tourism, industrial, and recreational sectors from 1987 to 2024.</strong></p><p>A monophonic oscillator represents the aggregated data for these sectors, with pitch increasing steadily over time to signify exponential growth. Accompanying visuals, derived from generative shaders and abstract imagery, contextualise these trends, linking historical development to auditory and visual elements.</p>"
              },
              {
                subtitle:'notification',
                delay: 0.6,
                content:"By simply pressing play on the YouTube video, viewers can explore how growth across these sectors shaped Mallorca’s transformation during this pivotal era."
              }
            ]
          },
        { 
            title: "dataTendency_undulating",
            video: null,
            background:"#E0E4E9",
            mapInfo:  
            {
              "location": "Mallorca (all municipalities)",
              "yearRange": "1997-2024, mensual",
              "source": [
             
               { 
                url: "https://ibestat.es/?lang=ca",
                title:"IBESTAT"
               },
                
              ]            },
            subsections: [
              {
                subtitle:'_origin',delay:0.2,
                color:"#0E23C1",
                icon: 'assets/title_origin.svg',
                content: " <p><strong>The Human Pressure Indicator (HPI) was developed to provide a more accurate measurement of population load in the Balearic Islands, accounting for both residents and tourists.</strong> Traditional demographic data often focused solely on residents, but the HPI incorporates seasonal fluctuations and resource strain caused by tourism. This index, introduced by the Institut d'Estadística de les Illes Balears (IBESTAT), uses data from airports, ports, and municipal registers to track daily population figures.</p>"
              },
              {
                subtitle:'_issue',delay:0.3,
                color:"#B40A47",
                icon: 'assets/title_issue.svg',
                content: "<p>The HPI reveals striking trends, such as seasonal surges during summer, when <strong>Mallorca’s population burden can exceed 1.47 million people on a single day</strong> (e.g., August 2022). These figures highlight the strain on local resources, infrastructure, and ecosystems, which require advanced planning and adaptive management.</p>"
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
                content:"Pushing play will trigger the next data visualisation and sonification, including an interactive visualisation of the HPI."
              }
            ]
          },
        { 
            title: "dataTendency_darkFigure",
            video:"https://burakkorkmaz.de/content/files/04_Posidonia.mp4",
            youtube:"https://www.youtube.com/embed/WkS4-OhSmzo",
            background:"#EEF1F4",
            mapInfo:  
            {
              "location": "Mallorca (all municipalities)",
              "yearRange": "sporadic since 2008",
              "source": [
               { 
                url: "https://imedea.uib-csic.es/en/",
                title:"IMEDEA"

               }
              ]
            },
            subsections: [
              {
                subtitle:'_origin',delay:0.2,
                color:"#0E23C1",
                icon: 'assets/title_origin.svg',
                content: "  <p><strong>The prairies of Posidonia oceanica, often called the “lungs of the Mediterranean,” play a crucial ecological role in oxygen production, CO₂ sequestration, and coastal protection. However, they face growing threats from human activities, including desalination, coastal development, and rising sea temperatures, which jeopardise biodiversity and the health of marine ecosystems.</strong></p>"
              },
              {
                subtitle:'_issue',delay:0.3,
                color:"#B40A47",
                icon: 'assets/title_issue.svg',
                content: "<p>While research institutions such as IMEDEA provide valuable data on Posidonia meadows, <strong>the information often carries a “dark figure” — unaccounted or underreported data.</strong> Much of the available information relies on sporadic volunteer scuba divers’ observations and visual surveys, often recorded in static formats like JPEG images. These inconsistencies hinder a comprehensive understanding of the meadows' condition and their long-term trends.</p>"
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
                content:"Simply pressing play on the YouTube video will trigger the next audiovisual segment, allowing viewers to explore the dynamics of Posidonia oceanica through sonification and abstract visualization."
              }
            ]
          },
        { 
            title: "dataTendency_deficient",
            video:"https://burakkorkmaz.de/content/files/05_Energia.mp4",
            youtube:"https://www.youtube.com/embed/4xEh_SqwPO8",
            background:"#E0E4E9",
            mapInfo:  
              {
                "location": "Mallorca (all municipalities)",
                "yearRange": "since 2010 (mensual)",
                "source": [
               { 
                url: "https://www.ine.es/",
                title:"INE"

               },
               { 
                url: "https://ibestat.es/?lang=ca",
                title:"IBESTAT"
               },
                
              ]              },
            subsections: [
              {
                subtitle:'_origin',delay:0.2,
                color:"#0E23C1",
                icon: 'assets/title_origin.svg',
                content: "  <p>Despite Mallorca’s abundant sunshine, its renewable energy investment has lagged behind, <strong>with renewable sources meeting only 25% of electricity demand during the summer months—far below mainland Spain. Historically, the island depended on imported coal and oil for energy, with seasonality and tourism driving sharp consumption increases. Between 1965 and 1988, electricity use rose dramatically from 496 KWh to 2,500 KWh.</strong> The introduction of a high-tension undersea cable in 2012 connected the island to the mainland’s national grid, alleviating some seasonal strain but deepening reliance on external resources.</p>"
              },
              {
                subtitle:'_issue',delay:0.3,
                color:"#B40A47",
                icon: 'assets/title_issue.svg',
                content: "<p>Renewable energy adoption remains sluggish despite some progress in photovoltaic energy production. The renewable sector still accounts for only a fraction of Mallorca’s energy mix. <strong>Efforts to modernise the grid and incorporate sustainable sources have been made by institutions like the Institut Balear de l'Energia (IBE), but structural inefficiencies persist.</strong> This underscores the urgent need for policies that prioritise sustainable, self-sufficient energy solutions tailored to the island’s unique conditions.</p>"
              },
              {
                subtitle:'_insight',delay:0.4,
                color:"#12A331",
                icon: 'assets/title_insights.svg',
                content:'<p>The stark contrast between fossil fuel dependency and renewable energy adoption highlights <strong>systemic inefficiencies in the energy infrastructure.</strong> These disparities serve as a case study for other regions grappling with similar challenges, emphasising the importance of proactive investment in sustainability.</p>'
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
                content:"The YouTube video offers an interactive experience: fossil fuel consumption is heard in the left audio channel, while renewable energy data plays on the right. Playing both together provides a full auditory representation of the energy dynamics."
              }
            ]
          },
        { 
            title: "dataTendency_hot",
            video:"https://burakkorkmaz.de/content/files/06_Caluroso.mp4",
            youtube:"https://www.youtube.com/embed/BQLTCrtvuus",
            background:"#EEF1F4",
            mapInfo:
              {
                "location": "Mallorca (all municipalities)",
                "yearRange": "since 1850 (annual)",
                "source": [{
                  title:"IPCC",
                  url:"https://atlas.climate.copernicus.eu/atlas"
                }]
              },
            subsections: [
              {
                subtitle:'_origin',delay:0.2,
                color:"#0E23C1",
                icon: 'assets/title_origin.svg',
                content: "<p>What we observe in the Balearic Islands, particularly in Mallorca, challenges the notion of economic growth driven by unlimited tourism. <strong>In a finite world, the pursuit of perpetual growth is unsustainable. If global consumption and emissions matched Mallorca’s levels, we’d likely face a worst-case scenario.</strong></p>"
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
                content:"Simply pressing play on the YouTube video triggers the audiovisual segment, using data sonification and generative visuals to immerse viewers in these dynamics."
              }
            ]
          },
    ];

    let sections =[];
    let currentSection = 0;
    // let stepProgress = new Array(steps.length).fill(0);
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

    // const handleScroll = () => {
    //   sections.forEach((section, index) => {
    //     stepProgress[index] = calculateScrollProgress(section);
    //   });
    //   stepProgress = [...stepProgress]; // Trigger reactivity
    // };

    let lineData = [];

    onMount(async () => {
      // setupIntersectionObserver();
        try {
          const raw = await d3.csv('data/iph.csv', d3.autoType);
          const parseDate = d3.timeParse("%m/%Y");
          lineData = raw.filter(d => ('' + d.month).length !== 4).map(d => ({ ...d, date: parseDate(d.month) })).sort((a,b)=>a.date-b.date);
        } catch (error) {
            console.error('Error loading CSV file:', error);
        }
      const observer = new IntersectionObserver(
          (entries) => {
            entries.forEach((entry) => {
              if (entry.isIntersecting) {
                // const index = sections.indexOf(entry.target);
                const index = parseInt(entry.target.getAttribute('data-index') || '0');
                currentSection = index;
              }
              // if (entry.isIntersecting) {
              //   const index = sections.indexOf(entry.target);
              //   if (index !== -1) {
              //     currentSection = index;
              //   }
              // }
            });
          },
          {
            root: null,
            rootMargin: '0px',
            threshold: 0.25,
          }
        );

          document.querySelectorAll('.scroll-section').forEach(section => {
            observer.observe(section);
          });

          // handleScroll(); // Initial calculation

          return () => {
            observer.disconnect();
            // window.removeEventListener('scroll', handleScroll);
          };
    
    });

    let isLoading = true;
    function handleIframeLoad() {
      isLoading = false;
    }
    // onDestroy(() => {
    //   window.removeEventListener('scroll', handleScroll);
    // });


    // function handleVisible(index) {
    //   console.log('play'+index)
    //   if (index==3 && audioRef) {
    //     audioRef.play()
    //   }
    //   else {
    //     videoRefs[index].play();
    //   }
    // }

    // function handleHidden(index) {
    //   console.log('pause'+index)
    //   if (index==3 && audioRef) {
    //     audioRef.pause();
    //   }
    //   else {
    //     videoRefs[index].pause();
    //   }
    // }
  
  </script>
    <div class="relative w-full lg:flex">
        <!-- Sticky sidebar -->
        <div class="w-full lg:w-1/3">
          {#each steps as section, i}
              <div class="scroll-section min-h-screen flex p-8 relative" style="background:{section.background}" bind:this={sections[i]} data-index={i}>
                  <div class="relative w-full py-16 px-8 flex flex-col gap-8 justify-center">
                    <div class="self-end text-xs">
                      <img src="assets/map_{i}.svg" class="w-[250px]" />
                      <p>LOCATION_<span class="text-[#0E23C1] mx-1">{section.mapInfo.location}</span></p>
                      <p>YEAR_RANGE_<span class="text-[#0E23C1] mx-1">{section.mapInfo.yearRange}</span></p>
                      <p>SOURCE_
                        <span class="">
                          {#each section.mapInfo.source as src,i}
                            <a class="mx-1 text-[#0E23C1]" href={src.url}>{src.title}{i==0 && section.mapInfo.source.length>1 ?',':''}</a>
                          {/each}
                        </span>
                      </p>
                    </div>
                    <h2 class="text-xl font-semibold text-[#0E23C1]"><span class="bg-white px-2">{steps[i].title}</span></h2>
                      {#each steps[i].subsections as subsection,subIndex}
                        <ScrollFade>
                          <div class="flex gap-2" style="color:{subsection.color}">
                            {#if subsection.subtitle!=='notification'}
                              <img class="w-4 h-4 mt-2" src={subsection.icon} />
                              <div>
                                  <h3 class="text-lg font-semibold">{subsection.subtitle}</h3>
                                  {@html subsection.content}
                                  {#if subsection.subtitle.split(" ")[0]=='_sonification'}
                                  <div class="mt-4 rounded-2xl bg-white px-2 py-4 flex items-start gap-2 text-[#545F71]">
                                    <img src="assets/notification.svg" class="w-4 h-4" alt='notification'/>
                                    <span class="text-xs">
                                      {@html steps[i].subsections[subIndex+1].content}
                                    </span>
                                  </div>
                                  {/if}
                                </div>
                               
                            {/if}
                          </div>
                        </ScrollFade>
                      {/each}
                      <!-- <div class="hidden lg:block">
                        <ScrollFade  
                          on:visible={() => handleVisible(i)}
                          on:hidden={() => handleHidden(i)}>
                            <div class="opacity-0 h-12"></div>
                        </ScrollFade>
                      </div> -->
                      <div class="block lg:hidden">
                        <ScrollFade>
                            {#if i==3 && lineData.length>0}
                              <div class="bg-black w-full h-[50vh] lg:h-screen">
                                <Chart data={lineData} />
                              </div>
                              {:else}
                                <!-- <Video index={i} videoSrc={steps[i].video} /> -->
                                {#if isLoading}
                                  <div class="">
                                    loading...
                                  </div>
                                {/if}
                                <iframe class="w-full h-full min-h-[400px]"
                                 src={steps[i].youtube} 
                                 on:load={handleIframeLoad}
                                 title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
                            {/if} 
                          </ScrollFade>
                      </div>
                  </div>
              </div>
              <div class="hidden lg:block h-[30vh]" style="background:{section.background}"></div>
          {/each}
        </div>
        <div class="hidden lg:block sticky top-0 left:0 h-screen w-full lg:w-2/3 flex items-center justify-center p-8 z-0 relative">
          <div class="flex items-center justify-center w-full h-full">
              {#if currentSection==3 && lineData.length>0}
                <div class="bg-black w-full h-full max-h-[80vh]">
                  <Chart data={lineData}/>
                </div>
                {:else}
              {#if steps[currentSection].video}
                <div class="text-white w-full h-0 overflow-hidden relative" style="padding-bottom:56.25%;">
                  <!-- <video preload="auto" controls class="w-full" src={steps[currentSection].video}>
                    <track kind="captions"/>
                  </video> -->
                  <!-- <Video index={currentSection} videoSrc={steps[currentSection].video} /> -->
                  {#if isLoading}
                    <div class="">
                      loading...
                    </div>
                  {/if}
                  <iframe 
                    class="w-full h-full top-0 left-0 absolute"
                     src={steps[currentSection].youtube}
                     on:load={handleIframeLoad}
                    title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
                </div>
                {/if}
              {/if} 
            </div>
      
        </div>
  </div>
  <!-- <svelte:window on:scroll={handleScroll} /> -->