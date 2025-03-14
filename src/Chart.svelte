<script>
    import { onMount, onDestroy} from 'svelte';
    import { tweened } from 'svelte/motion';
    import { linear } from 'svelte/easing';
    import * as d3 from 'd3';

    export let data;
    // export let progress;
    let width;
    let height;
    let audioRef;

    const margin = { top: 100, right: 50, bottom: 20, left: 100 };

    $: x = d3.scaleTime()
      .domain(d3.extent(data, d => d.date))
      .range([0, width-margin.left-margin.right]);

    $: y = d3.scaleLinear()
        .domain([0, d3.max(data, d => d.value)])
        .range([height-margin.top-margin.bottom, 0]);

    $: lineGenerator = d3.line()
        .x(d => x(d.date))
        .y(d => y(d.value))
        .curve(d3.curveCatmullRom);


    
    let pathRef;
    let pathLength;

    $: if (pathRef) pathLength = pathRef.getTotalLength();
    
    const handleAudioEnd = () =>{
        // progress.set(0, { duration: 0 });

    }
    let counter = 0;

    const progress = tweened(0, {
        duration: 82.5*1000,
        easing: linear
    });
    const handleStart= () => {
        progress.set(0, { duration: 0 });
        progress.set(1)
        // const timer = d3.interval(() => {
        //    counter+=1
        // }, 250);

        // onDestroy(() => {
        //     timer.stop();
        // });
    }
</script>

<audio preload="auto" class="absolute top-0 z-10 hidden" controls  bind:this={audioRef} on:ended={handleAudioEnd} on:play={handleStart}>
    <source src="/HumanPressureIndex.wav"  type="audio/wav">
</audio>

<div class="w-full h-full flex flex-col" >
   
    <div class="text-white w-full mt-8 flex flex-col items-center">
        <h3 class="text-2xl">Human Pressure Index in Mallorca</h3>
        <p>HPI per surface area (people/km<sup>2</sup>)</p>
    </div>
    <div class="flex-grow" bind:clientHeight={height} bind:clientWidth={width}>
        {#if audioRef && audioRef.paused}
            <button class="absolute top-1/2 left-1/2 border -translate-x-1/2 -translate-y-1/2 border-white p-4 z-10 hover:bg-white hover:text-black text-white text-2xl" on:click={()=> audioRef.play()}>Play</button>
        {/if}
        <svg {width} {height}>
            {#if width>0}
                <g transform="translate({margin.left},{height - margin.bottom-50})">
                    {#each d3.range(1997,2025) as year}
                        <text 
                            class="text-[0.7em]"
                            text-anchor="middle"
                            transform={`rotate(-45, ${x(new Date(year+'-01-01'))}, 0)`}
                            dominant-baseline="middle"
                            y={0}
                            x={x(new Date(year+'-01-01'))} 
                            fill="#fff">
                            {year}
                        </text>
                    {/each}
                </g>
                <g transform="translate({margin.left},0)" class="y-axis">
                    {#each d3.range(0,1300000,200000) as value}
                        <text                         
                            class="text-[0.8em]"
                         text-anchor="end" y={y(value)}  dx={-50} fill="#fff">{value==0 ? 0: d3.format(".2s")(value)}</text>
                    {/each}
                    <g  transform="translate(-30, 0)">
                        <rect x={-5} y={y(0)-5} width={10} height={10} fill="#fff" />
                        <rect  x={-5} y={y(1300000)-5} width={10} height={10} fill="#fff" />
                        <rect  x={x(new Date('2025-01-01'))-5} y={y(0)-5} width={10} height={10} fill="#fff" />
                        <line x1={0} x2={0} y1={y(0)} y2={y(1300000)} stroke="#fff" />
                        <line x1={0} x2={x(new Date('2025-01-01'))} y1={y(0)} y2={y(0)} stroke="#fff" />
                    </g>
    
                </g>
                <g transform="translate({margin.left},{margin.top})">
                    <path bind:this={pathRef}
                        d={lineGenerator(data)} fill="none" stroke="#fff"
                        stroke-dashoffset={pathLength - ($progress * pathLength)}
                        stroke-dasharray={pathLength} />
                    <!-- {#each data as d,i}
                            <circle cx={x(d.date)} cy={y(d.value)} r={5} fill='#fff' />
                    {/each} -->
                </g>
            {/if}
        </svg>
    </div>
</div>