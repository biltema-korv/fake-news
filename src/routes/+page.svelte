<script>
  const d = new Date();
  import favicon from '$lib/assets/favicon.svg';
	import { base } from '$app/paths';
  import { page } from '$app/stores';
  let polarbear="assets/polarbear.png"
  let place="assets/plats.png"
  let rent="assets/styrranta.png"
  let ostboll="assets/ostboll.png"
  let selectedcategory=$state("Alla")
  let news=$state({
    newstitle: ["Rostmackor dödar isbjörnarna.","Flintskallig lärare jagade elev efter misslyckat mattepass","Styrräntan höjs till 20 procent, stora förändringar på väg","Kalle Anka partiet får högt stöd i opinionen, lovar 'längre sovmorgon'","Elev risigt ute efter att spelat onlinespel med digital valuta","Påse av ostkrokar innehöll en ostboll"], 
    newsdescription: [
      'En ny studie publicerad av Hullaballu Universitetet visar att för varje rostmacka som rostas dör 3 isbjörnsfamiljer. Det kan få stora följder för framtiden av isbjörnarna, säger experter. En person säger: "Jag bryr mig då fan inte, det är ju jävligt gott."'
      ,"Älskad lärare Flintis Flintimer har jagat ut en elev ut ur skolan efter att de misslyckades med 3+4. Enligt källor svarade eleven blankt, som den stora fegisen den är."
      ,"Riksbankschefen Erik Thedéen säger att svenskar 'är horribla' på att hantera ekonomin, och att vi borde vara mer sparsamma. Därför höjs styrräntan från 1,75 procent upp till 20, en ökning på 18,25 procentenheter. Han påstår att det är för att få 'tillbaka kontroll' av den svenska ekonomin."
      ,"Bra nyheter kommer för Ankeborg, då det sägs att partiet 'Kalle Anka partiet' har fått 107.5% stöd, en ökning av 2.3 procentenheter från senaste mätningen. Mätningen utfördes av mig. 'Nu blir det garanterad vinst', säger jag. Rösta på oss för längre sovmorgon."
      ,"En elev har haft en dålig dag i skolan, då det upptäcktes att de spelade onlinespel för digital valuta. De har blivit skickad till psykisk sjukvård och ska observeras inom några dagar. Vi håller er uppdaterade."
      ,"Det ser knackigt ut för ostkrok entusiaster, därför att någon har rapporterat att det fanns en ostboll i deras påse med ostkrokar. Det här bryter mot många lagar, förmodligen."
    ], 
    newsimage: [polarbear,place,rent,place,place,ostboll],
    sendto: ['deepdive'],
    skribent: ['Jarl "Brödrost Förgörare" Bengtsson','Okänd Sponsrad Lärare','Rally Arne','Entusiastisk Kalle Anka Partist',"Big M","Ring Rost Ragnar"],
    categories: ['Klimat','Oroande','Ekonomi','Politik','Oroande','Ekonomi'],
    calenderday: [-1,10,'Ekonomi','Politik'],
  })
  function pickcategory(category) {
    selectedcategory=category;
  }

	let { children } = $props();
</script>



<main>
  <div class="wanga">
    <h1>Fallaciloqua</h1>
    <h3>Unbiased, factual, daily.</h3>
    <div class="separator"> </div>
  </div>

  <categories>
    <button class="category" onclick={() => pickcategory("Alla")}>Alla</button>
    <button class="category" onclick={() => pickcategory("Politik")}>Politik</button>
    <button class="category" onclick={() => pickcategory("Ekonomi")}>Ekonomi</button>
    <button class="category" onclick={() => pickcategory("Klimat")}>Klimat</button>
    <button class="category" onclick={() => pickcategory("Oroande")}>Oroande</button>
  </categories>
  <a class="yeah" href="games-list">Spela våra spel</a>
  
  <h3>Nuvarande kategori: {selectedcategory}</h3>
  
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
        <p class="rightsidestuff">yum yum</p>
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
    width: 60vw;
  }

  .newsarticles{
    margin: auto;
    width: 50vw;
    height: 10vh;
    /*overflow: hidden;*/
    text-align: left;
    justify-content: left;
    grid-template-columns: 1fr 1fr;
    display: flex;
  }

  .rightsidestuff{
    text-align: right;
    margin-left: auto;
    margin-right: 0;
    position: absolute;
    right: 2vw;
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

  h1{
    font-size: 6vh;
    font-family:'Times New Roman', Times, serif;
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
    padding: 0.5vh;
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
  .yeah{
    position: fixed;
    width: fit-content;
    text-align: right;
    display: block;
    right: 11vw;
    margin-left: 10vh;
    margin-right: auto;
  }
</style>
