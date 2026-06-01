<script>
    import { base } from '$app/paths';
</script>

<main>
    <a href="{base}/">Till huvudsidan</a>
    <a href="{base}/math-game">Mattespel</a>
    <a href="{base}/fortunecookie">Lyckokaka grejsemojs</a>
</main>

<style>

    a{
        justify-content: center;
        display: flex;
        font-size: 2vw;
        transition: transform 0.3s;
        color:white;
        padding: 1vh;
        width: fit-content;
        text-align: center;
        margin: auto;
    }
    a:hover{
        transform: scale(1.08);
    }

    :global(body) {
        color:white;
        font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        background-color: #2d2d30;
    }
</style>