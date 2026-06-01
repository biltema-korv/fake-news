<script>
  const d = new Date();
  import favicon from '$lib/assets/favicon.svg';
  import { base } from '$app/paths';
  import { onMount, tick } from 'svelte';
  
  const polarbear="assets/polarbear.png"
  const place="assets/plats.png"
  const rent="assets/styrranta.png"
  const ostboll="assets/ostboll.png"
  const icecram="assets/icecram.png"
  const copyright="assets/copyright.png"
  let temp=$state(21)
  let random=$state(Math.floor(Math.random() * 12))
  let randomweather=$state(Math.floor(Math.random() * 4))
  let icons=$state("")
  let titleSpin = $state(false)
  onMount(() => {
    if (randomweather<=1){
      icons="☀︎"
      temp=23-random/2
    }
    else if (randomweather==2){
      icons="☔︎︎"
      temp=13-random/2
    }
    else if (randomweather==3){
      icons="🌩"
      temp=17-random/2
    }
  });

  let selectedcategory=$state("Alla")
  let news=$state({
    newstitle: ["Rostmackor dödar isbjörnarna.","Flintskallig lärare jagade elev efter misslyckat mattepass","Styrräntan höjs till 20 procent, stora förändringar på väg","Kalle Anka partiet får högt stöd i opinionen, lovar 'längre sovmorgon'","Elev risigt ute efter att spelat onlinespel med digital valuta","Påse av ostkrokar innehöll en ostboll","Glassföretag byter bransch i Frankrike"], 
    newsdescription: [
      'En ny studie publicerad av Hullaballu Universitetet visar att för varje rostmacka som rostas dör 3 isbjörnsfamiljer. Det kan få stora följder för framtiden av isbjörnarna, säger experter. En person säger: "Jag bryr mig inte, det är ju sjukt gott."'
      ,"Älskad lärare Flintis Flintimer har jagat ut en elev ut ur skolan efter att de misslyckades med 3+4. Enligt källor svarade eleven blankt, som den stora fegisen den är."
      ,"Riksbankschefen Erik Thedéen säger att svenskar 'är horribla' på att hantera ekonomin, och att vi borde vara mer sparsamma. Därför höjs styrräntan från 1,75 procent upp till 20, en ökning på 18,25 procentenheter. Han påstår att det är för att få 'tillbaka kontroll' av den svenska ekonomin."
      ,"Bra nyheter kommer för Kalle Anka-partister, då det sägs att partiet 'Kalle Anka partiet' har fått 107.5% stöd, en ökning av 2.3 procentenheter från senaste mätningen. Mätningen utfördes av en Kalle Anka-partist. 'Nu blir det garanterad vinst', säger en Kalle Anka partist. 'Rösta på oss för längre sovmorgon.'"
      ,"En elev har haft en dålig dag i skolan, då det upptäcktes att de spelade onlinespel för digital valuta. De har blivit skickad till psykisk sjukvård och ska observeras inom några dagar. Vi håller er uppdaterade."
      ,"Det ser knackigt ut för ostkrok entusiaster, därför att någon har rapporterat att det fanns en ostboll i deras påse med ostkrokar. Det här bryter mot många lagar, förmodligen."
      ,"Efter den nyliga värmeböljan som slog till Frankrike och västra Europa, har alla glassföretag i Frankrike gått ihop och bestämt sig för att sälja vatten istället. 'Detta är för att glassarna smälter för snabbt och alla konsumenter skyller på företagen, inte vädret. Vi ser även en stor efterfrågan på vatten,' säger en representant för franska glassföretag."
    ], 
    newsimage: [polarbear,place,rent,copyright,place,ostboll,icecram],
    skribent: ['Jarl "Brödrost Förgörare" Bengtsson','Anonym Lärare','Rally Arne','Munk Filip',"Big M","Ring Rost Ragnar","Louis Simpleton"],
    categories: ['Klimat','Oroande','Ekonomi','Politik','Oroande','Oroande','Ekonomi'],
    calenderday: [-1,10,'Ekonomi','Politik'],
  })
  function pickcategory(category) {
    selectedcategory=category;
  }

	let { children } = $props();

  async function interact(where) {
    if (where==="title"){
      titleSpin = false;
      await tick();
      titleSpin = true;
    }
  }
</script>



<main>
  <div class="wanga">
    <button class:titlespin={titleSpin} onclick={() => interact("title")} onanimationend={() => titleSpin = false}>Fallaciloqua</button>
    <h3>Unbiased, factual, daily.</h3>
    <div class="separator"> </div>
  </div>
      <div class="temperature">
        <span class="icon">Väder om ett år: {icons}</span>
        <div class="temp-bar" aria-hidden="true">{temp}°C</div>
      </div>

  <categories>
    <button class="category" onclick={() => pickcategory("Alla")}>Alla</button>
    <button class="category" onclick={() => pickcategory("Politik")}>Politik</button>
    <button class="category" onclick={() => pickcategory("Ekonomi")}>Ekonomi</button>
    <button class="category" onclick={() => pickcategory("Klimat")}>Klimat</button>
    <button class="category" onclick={() => pickcategory("Oroande")}>Oroande</button>
  </categories>
  <a class="yeah" href="games-list">Spela våra spel</a>
  
  <h3 class="categoryheader">Nuvarande kategori: {selectedcategory}</h3>
  
  {#each news.newstitle as title, i}
    {#if selectedcategory === "Alla" || news.categories[i] === selectedcategory}
    <article class="article">
	    <a href="deepdive/?index={i}">{news.newstitle[i]}</a>
        <div class="newsarticles">
          <div class="textagain">
          <h3 class="desc">{news.newsdescription[i]}</h3>
          <h4 class="desc">Skriven av {news.skribent[i]}</h4> 
          <h4 class="calenderday">{d.getDate()}/{d.getMonth()+1}/{d.getFullYear()}</h4> 
        </div>
        <img alt="News Icon" src={news.newsimage[i]}>
        </div>
      <div class="separatornews"> </div>
    </article>
    {/if}
  {/each}

</main>

<style>

  .textagain{
    display: flex;
    flex-direction: column;
    line-height: 2.8vh
  }

  main {
    margin: auto;
  }

  .separator{
    border: solid 0.15vw white;
    margin: auto;
    width: 40vw;
    /*overflow: hidden;*/
    text-align: center;
  }

  .separatornews{
    border: solid 0.15vw whitesmoke;
    margin: auto;
    width: 60vw;
    /*overflow: hidden;*/
    margin-top: 40vh;
    position: relative;
  }

  img{
    width:35vw;
    height:46vh;
    display: flex;
    justify-content: right;
    position: relative;
    margin: auto;
    border-radius: 3vh;
    
  }
  .wanga{
    margin: auto;
    width: 40vw;
    height: 10vh;
    /*overflow: hidden;*/
    text-align: center;
    line-height: 1vh;
  }

  .article{
    width: 75vw;
    margin: auto;
  }

  .newsarticles{
    margin: auto;
    width: 60vw;
    height: 12vh;
    /*overflow: hidden;*/
    text-align: left;
    justify-content: center;
    grid-template-columns: 1fr 1fr;
    display: flex;
  }
  
  categories{
    margin: auto;
    width: 50vw;
    height: 10vh;
    text-align: top;
    line-height: 0px;
    grid-template-columns: repeat(1, 3vw);
    display: flex;
  }

  :global(body) {
    color:white;
    font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    background-color: #2d2d30;
  }

  button{
    color: white;
    font-size: 6vh;
    font-family:'Times New Roman', Times, serif;
    background-color: transparent;
    border: transparent;
    width: fit-content;
    font-weight: 600;
  }
  button:hover{
    transform: scale(1.03);
  }
  h3{
    color: #B2B2B2;
    font-size: 2.5vh;
    flex-direction: column;
    display: flex;
  }
  h4{
    color: #B2B2B2;
    font-size: 2vh;
    flex-direction: column;
    display: flex;
  }
  a{
    color: white;
    font-size: 3.5vh;
    text-align: center;
    margin:auto;
    display: flex;
    position: relative;
    justify-content: center;
    transition: transform 0.3s;
    padding: 1vh;
    align-self: center;
    width: fit-content;
  }

  .desc{
    color: #B2B2B2;
    font-size: 2.5vh;
    text-align: left;
    width:40vh;
  }
  .category{
    font-size:3.5vh;
    width:10vw;
    height:3vw;   
    text-align: center;
    border-radius: 5vw;
    border: solid 0.2vw white;
    line-height: 5vh;
    color:white;
    background-color: #2d2d30;
    font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    margin: 1vh;
    transition: transform 0.3s;
  }
  .category:hover {
    transform: scale(1.1);
    border: solid 0.3vw gray;
    color:gray;
    box-shadow: 0 0 12px gray;
  }
  a:hover {
    transform: scale(1.05);
    color:gray;
  }
  .temperature{
    position: relative;
    display: inline-block;
    width: 25vh;
    height: 4vh;
    font-size: 3vh;
  }
  .temperature .temp-bar{
    position: absolute;
    top: 50%;
    left: 100%;
    transform: translateY(-50%);
    transform-origin: left center;
    transition: transform 0.16s ease, opacity 0.16s ease;
    opacity: 0;
    background: rgba(255,255,255,.08);
    color: white;
    padding: .4vh .6vh;
    border-radius: .4vh;
    pointer-events: none;
    z-index: 10;
  }
  .temperature:hover .temp-bar,
  .temperature:focus-within .temp-bar{
    transform: translate(6px, -50%);
    opacity: 1;
  }
  .yeah{
    position: absolute;
    width: fit-content;
    text-align: right;
    display: block;
    right: 0;
    margin-left: auto;
    margin-right: 10vh;
  }
  .categoryheader{
    position: absolute;
    top: auto;
  }

  .titlespin {
    animation: spin-title 0.6s ease;
  }

  @keyframes spin-title {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
  }
</style>
