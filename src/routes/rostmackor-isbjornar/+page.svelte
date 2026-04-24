<script>
    let polarbear="/assets/polarbear.png"
    let news=$state({
        newstitle: ["Rostmackor dödar isbjörnarna!","gork"], 
        newsdescription: ['En ny studie publicerad av Hullaballu Universitetet visar att för varje rostmacka som rostas dör 3 isbjörnsfamiljer. Det kan få stora följder för framtiden av isbjörnarna, säger experter. En person säger: "Jag bryr mig då fan inte, det är ju jävligt gott."'], 
        newsimage: [polarbear],
        sendto: ['rostmackor-isbjornar'],
        newsdescription2: ['Skribent Jarl "Brödrost Förgörare" Bengtsson berättar att brödrostar alltid har varit emot honom, och han har misstänkt att något var fel. Det ledde till att han gjorde en expedition till Arktis, och märkte att flera tusentals isbjörnar var döda. Han provade brödrosten, och såg 3 isbjörnsfamiljer dö på smällen. Nu vill han göra brödrostar olagliga, för att rädda isbjörnarna, och "äntligen" förgöra brödrostarna. Han uppmanar alla att äta orostat bröd.']
    })
    import favicon from '$lib/assets/favicon.svg';
	import { base } from '$app/paths';

	let { children } = $props();
</script>

<main> 
    <article>
	    <h1>{news.newstitle[0]}</h1>
        <div class="newsarticles">
            <h3 class="desc">{news.newsdescription[0]}</h3>
            <img alt="News Icon" src={news.newsimage[0]}>
            <h3 class="desc">{news.newsdescription2[0]}</h3>
        </div>
    </article>

  	<link rel="icon" href={favicon} />
</main>

<style>
    article{
        width: 50vw;
    }
    img{
        width:50vw;
        height:50vh;
        justify-content: left;
        position: left;
        margin: auto;
        display: flex;
        border-radius: 8vh;
    }
</style> 