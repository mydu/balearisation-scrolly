<script>
    import Scrollytelling from './Scrollytelling.svelte';
    import intro from './assets/intro.png'
  </script>
  
  <main class="w-full h-screen m-0 relative">
    <div class="h-screen">
        <img class="w-full" src={intro} />
        <div class="mx-auto p-4 w-3/4">

            <h1 class="font-bold text-xl">Unveiling Reciprocal Interactions and Dependencies at the Crossroads of Mass Tourism and the Climate Crisis</h1>
            <p>
                This audiovisual project is the result of in-depth research undertaken as part of the Goethe auf Mallorca artistic residency at Casa Planas in Palma de Mallorca, facilitated by the Goethe Institut Barcelona. To foster a more data-driven, explanatory, and exploratory approach, this scrollytelling, as an output of ongoing and iterative research, segments the narrative into distinct sections. Each section integrates data sonification, soundscapes, generative imagery, and archival footage. Notably, all the data trends referenced are reflected through data sonification, while the accompanying visuals partially represent these data points. The visuals also offer a conceptual interpretation of the diffuse economy of tourism, incorporating abstract imagery, architectural generative approaches, and archival footage from the extensive archive of Casa Planas. This segmentation transforms the traditional linear video into an interactive and explorative experience.
            </p>
        </div>
    </div>
    <!-- <div class="absolute inset-0 bg-gray-800 opacity-80"></div> -->
    <Scrollytelling />
  </main>