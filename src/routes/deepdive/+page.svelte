<script>
    import { onMount } from 'svelte';
    let polarbear="assets/polarbear.png"
    let place="assets/plats.png"
    let rent="assets/styrranta.png"
    let ostboll="assets/ostboll.png"
    
    // Get the article index from the URL query parameter
    let articleIndex = $state(0);
    onMount(() => {
        const current = parseInt(new URLSearchParams(window.location.search).get('index') || '0', 10);
        articleIndex = Number.isNaN(current) ? 0 : current;
    });
    let news=$state({
        newstitle: ["Rostmackor dödar isbjörnarna.","Flintskallig lärare jagade elev efter misslyckat mattepass","Styrräntan höjs till 20 procent, stora förändringar på väg","Kalle Anka partiet får högt stöd i opinionen, lovar 'längre sovmorgon'","Elev risigt ute efter att spelat onlinespel med digital valuta","Påse av ostkrokar innehöll en ostboll"], 
        newsdescription: ['En ny studie publicerad av Hullaballu Universitetet visar att för varje rostmacka som rostas dör 3 isbjörnsfamiljer. Det kan få stora följder för framtiden av isbjörnarna, säger experter. En person säger: "Jag bryr mig då fan inte, det är ju jävligt gott."'
            ,"Älskad lärare Flintis Flintimer har jagat ut en elev ut ur skolan efter att de misslyckades med 3+4. Enligt källor svarade eleven blankt, som den stora fegisen den är."
            ,"Riksbankschefen Erik Thedéen säger att svenskar 'är horribla' på att hantera ekonomin, och att vi borde vara mer sparsamma. Därför höjs styrräntan från 1,75 procent upp till 20, en ökning på 18,25 procentenheter. Han påstår att det är för att få 'tillbaka kontroll' av den svenska ekonomin."
            ,"Bra nyheter kommer för Ankeborg, då det sägs att partiet 'Kalle Anka partiet' har fått 107.5% stöd, en ökning av 2.3 procentenheter från senaste mätningen. Mätningen utfördes av mig. 'Nu blir det garanterad vinst', säger jag. Rösta på oss för längre sovmorgon."
            ,"En elev har haft en dålig dag i skolan, då det upptäcktes att de spelade onlinespel för digital valuta. De har blivit skickad till psykisk sjukvård och ska observeras inom några dagar. Vi håller er uppdaterade."
            ,"Det ser knackigt ut för ostkrok entusiaster, därför att någon har rapporterat att det fanns en ostboll i deras påse med ostkrokar. Det här bryter mot många lagar, förmodligen."
        ], 
        newsimage: [polarbear,place,rent,place,place,ostboll],
        sendto: ['rostmackor-isbjornar'],
        newsdescription2: [
            'Skribent Jarl "Brödrost Förgörare" Bengtsson berättar att brödrostar alltid har varit emot honom, och han har misstänkt att något var fel. Det ledde till att han gjorde en expedition till Arktis, och märkte att flera tusentals isbjörnar var döda. Han provade brödrosten, och såg 3 isbjörnsfamiljer dö på smällen. Nu vill han göra brödrostar olagliga, för att rädda isbjörnarna, och "äntligen" förgöra brödrostarna. Han uppmanar alla att äta orostat bröd.'
            ,'jag glum'
            ,'HJÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄLP'
        ]})
    import favicon from '$lib/assets/favicon.svg';
	import { base } from '$app/paths';

	let { children } = $props();
</script>

<main> 
    <article>
	    <h1>{news.newstitle[articleIndex]}</h1>
        <div class="newsarticles">
            <h3 class="desc">{news.newsdescription[articleIndex]}</h3>
            <img alt="News Icon" src={news.newsimage[articleIndex]}>
            <h3 class="desc">{news.newsdescription2[articleIndex]}</h3>
        </div>
    </article>

  	<link rel="icon" href={favicon} />
</main>

<style>
    :global(body) {
        color:white;
        font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        background-color: #2d2d30;
    }

    article{
        width: 50vw;
    }
    img{
        width:40vw;
        height:50vh;
        justify-content: left;
        position: left;
        margin: auto;
        display: flex;
        border-radius: 8vh;
    }
</style> 