<script>
    import Scrollytelling from './Scrollytelling.svelte';
  </script>
  
  <main class="w-full h-screen m-0 relative" style="font-family: 'Montserrat', sans-serif;">
    <img class="w-full" src="assets/intro.png" />
    <div class="">
        <div class="mx-auto flex flex-col h-screen">
            <div class="flex-grow flex lg:items-center justify-center">
                <div class="w-full p-8 lg:w-1/2">

                    <h1 class="font-bold text-xl text-[#0E23C1]">Unveiling Reciprocal Interactions and Dependencies at the Crossroads of Mass Tourism and the Climate Crisis</h1>
                    <p>
                        This audiovisual project is the result of in-depth research undertaken as part of the Goethe auf Mallorca artistic residency at Casa Planas in Palma de Mallorca, facilitated by the Goethe Institut Barcelona.
                    </p>
                    <p class="mt-8">
                        To foster a more data-driven, explanatory, and exploratory approach, this scrollytelling, as an output of ongoing and iterative research, segments the narrative into distinct sections. Each section integrates data sonification, soundscapes, generative imagery, and archival footage. Notably, all the data trends referenced are reflected through data sonification, while the accompanying visuals partially represent these data points. The visuals also offer a conceptual interpretation of the diffuse economy of tourism, incorporating abstract imagery, architectural generative approaches, and archival footage from the extensive archive of Casa Planas. This segmentation transforms the traditional linear video into an interactive and explorative experience.
                    </p>
                </div>
            </div>
        </div>
    </div>
    <!-- <div class="absolute inset-0 bg-gray-800 opacity-80"></div> -->
    <Scrollytelling />
    <footer>
      <div class="bg-[#EEF1F4] w-full py-24 flex justify-center items-center gap-16">
          <a href="" target="_blank"><img class="h-20" src="assets/logo_casaplanas.png" /></a>
          <a href="" target="_blank"><img class="h-20"  src="assets/Logo_COSTA_PositivoNegro_transp.png" /></a>
          <a href="" target="_blank"><img class="h-16"  src="assets/gi_logo_horizontal_green-v2-scaled.jpg" /></a>
             <a href="" target="_blank"><img class="h-16"   src="assets/header-logo-es.png" /></a>
      </div>
    </footer>
  </main>