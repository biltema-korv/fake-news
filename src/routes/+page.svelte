<script>
  import favicon from '$lib/assets/favicon.svg';
	import { base } from '$app/paths';
  let polarbear="assets/polarbear.png"
  let place="assets/plats.png"
  let rent="assets/styrranta.png"
  let selectedcategory=$state("Alla")
  let news=$state({
    newstitle: ["Rostmackor dödar isbjörnarna.","Flintskallig lärare jagade elev efter misslyckat mattepass","Styrräntan höjs till 20 procentenheter","Kalle Anka partiet får högt stöd i opinionen, lovar 'längre sovmorgon'"], 
    newsdescription: ['En ny studie publicerad av Hullaballu Universitetet visar att för varje rostmacka som rostas dör 3 isbjörnsfamiljer. Det kan få stora följder för framtiden av isbjörnarna, säger experter. En person säger: "Jag bryr mig då fan inte, det är ju jävligt gott."'
      ,"Älskad lärare Flintis Flintimer har jagat ut en elev ut ur skolan efter att de misslyckades med 3+4. Enligt källor svarade eleven blankt, som den stora fegisen den är."
      ,"Riksbankschefen Erik Thedéen säger att svenskar 'är horribla' på att hantera ekonomin, och att vi borde vara mer sparsamma. Därför höjs styrräntan från 1,75 procentenheter upp till 20, för att få 'tillbaka kontroll' av svenska ekonomin."
    ], 
    newsimage: [polarbear,place,rent],
    sendto: ['rostmackor-isbjornar'],
    skribent: ['Jarl "Brödrost Förgörare" Bengtsson','Okänd Sponsrad Lärare','Rally Arne','Entusiastisk Kalle Anka Partist'],
    categories: ['Klimat','Oroande','Ekonomi','Politik']
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
  
  {#each news.newstitle as title, i}
    {#if selectedcategory === "Alla" || news.categories[i] === selectedcategory}
    <article class="article">
	    <a href="{news.sendto[i]}/">{news.newstitle[i]}</a>
        <div class="newsarticles">
          <div class="textagain">
          <h3 class="desc">{news.newsdescription[i]}</h3>
          <h4 class="desc">Skapad av {news.skribent[i]}</h4> 
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
    border: solid 0.15vw white;
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
    line-height: 1vh
  }

  .newsarticles{
    margin: auto;
    width: 50vw;
    height: 10vh;
    /*overflow: hidden;*/
    text-align: left;
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
    overflow-x: auto;
  }

  :global(body) {
    color:white;
    font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  }

  :global(body) {
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
    transition: transform 0.5s;
  }
  .category:hover {
    transform: scale(1.1);
  }
  </style>
