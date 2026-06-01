<script>
    import { onMount } from 'svelte';
    const polarbear="assets/polarbear.png"
    const place="assets/plats.png"
    const rent="assets/styrranta.png"
    const ostboll="assets/ostboll.png"
    const icecram="assets/icecram.png"
    const copyright="assets/copyright.png"
    
    // Get the article index from the URL query parameter
    let articleIndex = $state(-1);
    onMount(() => {
        const current = parseInt(new URLSearchParams(window.location.search).get('index') || '0', 10);
        articleIndex = Number.isNaN(current) ? 0 : current;
    });
    let news=$state({
        newstitle: ["Rostmackor dödar isbjörnarna.","Flintskallig lärare jagade elev efter misslyckat mattepass","Styrräntan höjs till 20 procent, stora förändringar på väg","Kalle Anka partiet får högt stöd i opinionen, lovar 'längre sovmorgon'","Elev risigt ute efter att spelat onlinespel med digital valuta","Påse av ostkrokar innehöll en ostboll","Glassföretag byter bransch i Frankrike"], 
        newsdescription: ['En ny studie publicerad av Hullaballu Universitetet visar att för varje rostmacka som rostas dör 3 isbjörnsfamiljer. Det kan få stora följder för framtiden av isbjörnarna, säger experter. En person säger: "Jag bryr mig inte, det är ju sjukt gott."'
            ,"Älskad lärare Flintis Flintimer har jagat ut en elev ut ur skolan efter att de misslyckades med 3+4. Enligt källor svarade eleven blankt, som den stora fegisen den är."
            ,"Riksbankschefen Erik Thedéen säger att svenskar 'är horribla' på att hantera ekonomin, och att vi borde vara mer sparsamma. Därför höjs styrräntan från 1,75 procent upp till 20, en ökning på 18,25 procentenheter. Han påstår att det är för att få 'tillbaka kontroll' av den svenska ekonomin."
            ,"Bra nyheter för Kalle Anka-partister, då det sägs att partiet 'Kalle Anka partiet' har fått 107.5% stöd, en ökning av 2.3 procentenheter från senaste mätningen. Mätningen utfördes av en Kalle Anka-partist. 'Nu blir det garanterad vinst', säger en Kalle Anka partist. 'Rösta på oss för längre sovmorgon.'"
            ,"En elev har haft en dålig dag i skolan, då det upptäcktes att de spelade onlinespel för digital valuta. De har blivit skickad till psykisk sjukvård och ska observeras inom några dagar. Vi håller er uppdaterade."
            ,"Det ser knackigt ut för ostkrok entusiaster, därför att någon har rapporterat att det fanns en ostboll i deras påse med ostkrokar. Det här bryter mot många lagar, förmodligen."
            ,"Efter den nyliga värmeböljan som slog till Frankrike och västra Europa, har alla glassföretag i Frankrike gått ihop och bestämt sig för att sälja vatten istället. 'Detta är för att glassarna smälter för snabbt och alla konsumenter skyller på företagen, inte vädret. Vi ser även en stor efterfrågan på vatten,' säger en representant för franska glassföretag."

        ], 
        newsimage: [polarbear,place,rent,copyright,place,ostboll,icecram],
        sendto: ['rostmackor-isbjornar'],
        skribent: ['Jarl "Brödrost Förgörare" Bengtsson','Anonym Lärare','Rally Arne','Munk Filip',"Big M","Ring Rost Ragnar","Louis Simpleton"],
        newsdescription2: [
            'Skribent Jarl "Brödrost Förgörare" Bengtsson berättar att brödrostar alltid har varit emot honom, och han har misstänkt att något var fel. Det ledde till att han gjorde en expedition till Arktis, och märkte att flera tusentals isbjörnar var döda. Han provade brödrosten, och såg 3 isbjörnsfamiljer dö på smällen. Nu vill han göra brödrostar olagliga, för att rädda isbjörnarna, och "äntligen" förgöra brödrostarna. Han uppmanar alla att äta orostat bröd.'
            ,'Detta kommer ha stora konsekvenser för lärare landet runt.'
            ,'Vi kommer uppdatera och berätta vilka konsekvenser detta tillför den svenska ekonomin senare. Fråga inte när.'
            ,'Ingen vet vad Kalle Anka partiet står för bortsett från längre sovmorgon, och inte ens det vet vi vad det innebär exakt. Trots det leder partiet stort. Källan är pålitlig, därför att Kalle Anka-partisten lovade på sitt hus. Vi kommer diskutera ytterligare med dem i deras lägenhet senare i veckan, kom tillbaka då.'
            ,'Spela inte onlinespel på skolan. Eller kanske inte alls.'
            ,'Vi har efterfrågat en kommentar från alla ostkrok producerare i landet, och för att veta vad de har för åtgärder i plats så att ingen någonsin hamnar i denna situation igen.'
            ,'Det finns röster som kallar för revolution i Frankrike på grund av detta, vilket inte är väldigt förvånande.'
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
            <h4 class="desc">Skriven av {news.skribent[articleIndex]}</h4> 
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