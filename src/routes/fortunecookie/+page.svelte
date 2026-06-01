<script>
	import { base } from '$app/paths';
    let randomize=$state(0)
    let text=$state("")
    let gork=$state(false)

    let lef="assets/fortunoscookikosderecha.png"
    let riught="assets/fortunoscookikosizquierda.png"

    function handleSubmit(){
        gork+=1
        if (gork>3){
            gork=0
        }
        if (gork===3){
        let random=Math.floor(Math.random() * 26)
        console.log(random)
        if (random===1) text="Du har fem dagar kvar."
        else if (random===2) text="Akta dig."
        else if (random===3) text="Du kommer få bra resultat på nästa prov."
        else if (random===4) text="De kommer inte hitta det."
        else if (random===5) text="Någon ser upp till dig."
        else if (random===6) text="Ignorera förra lycka."
        else if (random===7) text="Du behöver inte vara snabbare än björnen, bara snabbare än kompisen."
        else if (random===8) text="Jag vill inte svara."
        else if (random===9) text="Sätt allt på rött."
        else if (random===10) text="Din inkomst kommer att öka."
        else if (random===11) text="Det är dags att prova något nytt."
        else if (random===12) text="När du lämnar huset imorgon på morgonen, gå åt höger direkt."
        else if (random===13) text="Bra saker kommer till dem som väntar."
        else if (random===14) text="Njut av livet."
        else if (random===15) text="Du kan läsa."
        else if (random===16) text="Om jorden inte är platt, varför är alla bilder av jorden platta?"
        else if (random===17) text="Låna pengar från en pessimist."
        else if (random===18) text="Jag kommer inte ihåg vad jag skulle säga."
        else if (random===19) text="Du skulle lyckas inom sjukvård."
        else if (random===20) text="Du kanske spenderar lite väl mycket."
        else if (random===21) text="Det är lätt att simma. Men att hålla sig flytande är svårare."
        else if (random===22) text="Vädret är fint."
        else if (random===23) text="Välkomna förändring."
        else if (random===24) text="Du kan behålla en hemlighet."
        else if (random===25) text="37°14′0″N 115°48′30″W"
        else text="Du kommer missa bussen."
        }
    }
</script>

<main>
    <a class="yeah" href="{base}/">Gå till huvudsidan</a>
    <a class="yeah" href="{base}/games-list">Gå till spellista</a>
    <h1>Fortune Cookie Game</h1>
    <button onclick={() => handleSubmit()}>Öppna lyckokakan</button>
    <same>
        <img alt="Peanut Right" src={lef} class:leftMove={gork==3} class:shakeleft={gork==2}>
        <img alt="Peanut Left" src={riught} class:rightMove={gork==3} class:shakeright={gork==1}>
        <p class="fortune" class:fadeIn={gork==3} class:fadeOut={gork==0}>{text} </p>
    </same>

</main>

<style>
    :global(body) {
        color:white;
        font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        background-color: #2d2d30;
        /*filter: hue-rotate(180deg)*/
    }

    same{
        display: grid;
        justify-content: center;
        position: relative;
    }
    img{
        grid-column: 1;
        grid-row: 1;
        transition: transform 0.3s;
    }

    .fortune{
        width: 10vw;
        height: fit-content;
        justify-content: center;
        text-align: center;
        
        margin-left: 8vw;
        margin-top: -15vw;
        z-index: -1;
        background-color: white;
        border-radius: 0.5vw;
        color: black;
        padding: 0.12vw;
        transition: opacity 0.2s;
        opacity: 0;
    }

    .leftMove {
        transform: translateX(10vw) translateY(1vw) rotate(30deg);
    }

    .rightMove {
        transform: translateX(-10vw) translateY(1vw) rotate(-30deg);
    }

    .shakeleft {
        animation: shakeleft 0.2s;
    }

    .shakeright {
        animation: shakeright 0.2s;
    }
    @keyframes shakeleft {
        0%   { transform: translateY(0); }
        50%  { transform: translateY(1vw) translateX(1vw); }
        100% { transform: translateY(0); }
    }

    @keyframes shakeright {
        0%   { transform: translateY(0); }
        50%  { transform: translateY(-1vw) translateX(-1vw); }
        100% { transform: translateY(0); }
    }

    .fadeIn {
        opacity: 1;
    }

    .fadeOut {
        opacity: 0;
    }

    button{
        width: 8vw;
        margin: auto;
        background-color: #2d2d30;
        color: white;
        border-color: white;
        border-radius: 0.3vw;
        z-index: 100;
    }

    .yeah{
        transition: transform 0.3s;
        color:white;
        justify-content: center;
        margin: auto;
        text-align: center;
        flex-direction: column;
    }

    main{
        justify-content: center;
        position: relative;
        display: flex;
        text-align: center;
        margin: auto;
        flex-direction: column;
        width: fit-content;
    }
</style>