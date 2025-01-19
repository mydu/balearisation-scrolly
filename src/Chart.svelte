<script>
    import { onMount, onDestroy} from 'svelte';
    import { tweened } from 'svelte/motion';
    import { linear } from 'svelte/easing';
    import * as d3 from 'd3';

    export let data;
    $: console.log(data)
    let audioRef; 
    let width;
    let height;

    const margin = { top: 50, right: 50, bottom: 50, left: 50 };

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

    // onMount(() => {
    //     audioRef.play()
    // });

    const handleAudioEnd = () =>{
        // progress.set(0, { duration: 0 });

    }
    let counter = 0;

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

    const progress = tweened(0, {
        duration: 82.5*1000,
        easing: linear
    });
    
    let pathRef;
    let pathLength;

    $: if (pathRef) pathLength = pathRef.getTotalLength();
</script>

<audio preload="auto" class="absolute top-0 z-10 hidden"  controls bind:this={audioRef} on:ended={handleAudioEnd} on:play={handleStart}>
    <source src="/HumanPressureIndex.wav"  type="audio/wav">
</audio>
{#if audioRef && audioRef.paused}
    <button class="absolute top-1/2 left-1/2 border border-white p-4 z-10 text-white text-2xl" on:click={()=> audioRef.play()}>Play</button>
{/if}
<div class="w-full h-full" bind:clientHeight={height} bind:clientWidth={width}>
    <svg {width} {height}>
        {#if width>0}
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