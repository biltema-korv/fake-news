<script>
    let written=$state("")
    let math1=$state(0)
    let operations=$state(0)
    let math2=$state(0)
    let result=$state(0)
    let resulttext=$state("")
    let streak=$state(0)
    let difficultysetting=$state("Normal") 
    let range=$state(10)
    import { base } from '$app/paths';

    math1=Math.random() * range  
    let random=$state(Math.floor(Math.random() * 3))
    math2=Math.random() * range
    if (random===0) operations="+", math1=math1*10, math2=math2*10, result=Math.floor(math1)+Math.floor(math2)
    else if (random===1) operations="-", math1=math1*10, math2=math2*10, result=Math.floor(math1)-Math.floor(math2)
    else if (random===2) operations="*", result=Math.floor(math1)*Math.floor(math2)

    
    function handleSubmit(){
        if (written == result) streak+=1, resulttext=`Congratulations you got me jumping for joy!!!!!!!!!` 
        else if (written == 69) resulttext="nice", streak=0
        else if (written == 67) resulttext="six seven six seven six seven ", streak=0
        else resulttext="The loser store called, they're running out of YOU!", streak=0

        randomize()
    }

    function randomize(){
        written=""
        math1=Math.random() * range
        random=Math.floor(Math.random() * 3)
        math2=Math.random() * range
        if (random===0) operations="+", math1=math1*10, math2=math2*10, result=Math.floor(math1)+Math.floor(math2)
        else if (random===1) operations="-", math1=math1*10, math2=math2*10, result=Math.floor(math1)-Math.floor(math2)
        else if (random===2) operations="*", result=Math.floor(math1)*Math.floor(math2)
    }

    function difficulty(which){
        if (which=="Easy") range=5, difficultysetting="Easy"
        else if (which=="Normal") range=10, difficultysetting="Normal"
        else if (which=="Hard") range=30, difficultysetting="Hard"
        else if (which=="baby") range=10000, difficultysetting="Baby Mode"
        streak=0
        resulttext=""
        randomize()
    }

        /*else if (random===3) {
            operations="/";
            result=math1/math2
        }

    /*function mathematics(){*/
        /*math1=Math.random() * 10      
        let random=Math.floor(Math.random() * 3)
        math2=Math.random() * 10
        if (random===0)   {
            operations="+";
            result=Math.floor(math1*10+math2*10);
        }
        else if (random===1) {
            operations="-";
            result=Math.floor(math1*10-math2*10);
        }
        else if (random===2) {
            operations="*";
            result=Math.floor(math1*math2*10)
        }/*
        /*else if (random===3) {
            operations="/";
            result=math1/math2
        }/*
    /*}*/
</script>

<main>
    <a class="yeah" href="{base}/">Gå till huvudsidan</a>
    <a class="yeah" href="{base}/games-list">Gå till spellista</a>
    <h1>Math Game</h1>

    <button class="category" onclick={() => difficulty("Easy")}>Easy</button>
    <button class="category" onclick={() => difficulty("Normal")}>Normales</button>
    <button class="category" onclick={() => difficulty("Hard")}>Muy Dificil</button>
    <button class="category" onclick={() => difficulty("baby")}>Baby Mode</button>
    <h2>Current Difficulty: {difficultysetting}</h2>
    <h2>{streak} correct in a row</h2>
    <h3>{Math.floor(math1)} {operations} {Math.floor(math2)}</h3>
    <h3>= {written}</h3>
    <input type="number" bind:value={written}>
    <button onclick={() => handleSubmit()}>Skicka in svar</button>
    <h2>{resulttext}</h2>
</main>

<style>

    main{
        justify-content: center;
        position: relative;
        display: flex;
        text-align: center;
        margin: auto;
        flex-direction: column;
        width: 20vw;
    }
    :global(body) {
        color:white;
        font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        background-color: #2d2d30;
    }
    .yeah{
        transition: transform 0.3s;
        color:white;
        width: fit-content;
        font-size: 3vh;
        justify-content: center;
        margin: auto;
    }
    .yeah:hover{
        transform: scale(1.08);
        color:gray;
    }
    button{
        width: fit-content;
        margin: auto;
    }
    
</style>