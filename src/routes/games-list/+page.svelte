<script>
    import { base } from '$app/paths';
</script>

<main>
    <a href="{base}/math-game">Mattespel</a>
    <a href="{base}/fortunecookie">Lyckokaka grejsemojs</a>
</main>

<style>

    a{
        justify-content: center;
        display: flex;
        font-size: 2vw;
        transition: transform 0.3s;
    }
    a:hover{
        transform: scale(1.05);
    }

    :global(body) {
        color:white;
        font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        background-color: #2d2d30;
    }
</style>