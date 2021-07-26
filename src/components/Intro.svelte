<script>
    import { fade } from 'svelte/transition';
    export let intro = true;

    let titles = [
        "Hobbyist Programmer",
        "Furry",
        "Artist"
    ]
</script>

<div class:intro transition:fade>
    <div>
        <div class="mini">Hi, I'm</div>
        <div class="header orange">Malachi Hargreaves</div>
        <div class="mini">a</div>
        <div class="title orange">Hobbyist Programmer</div>
    </div>
</div>

<style>
    .intro {
        justify-content: center;
        text-align: center;
        display: flex;
        padding-top: 38vh;
    }

    .header {
        font-size: 4rem;
        font-weight: 600;
    }

    .title {
        font-size: 3rem;
    }

    .mini {
        font-size: 2.5rem;
    }

    .orange {
        color: var(--fox-orange);
    }

    @media only screen and (max-width: 700px) {
        .header {
            font-size: 2rem;
            font-weight: 600;
        }

        .title {
            font-size: 1rem;
        }
    }
</style>
