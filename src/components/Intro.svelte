<script lang="ts">
    import { fade, fly } from 'svelte/transition';
    export let intro = true;

    let index = 0;
    let titles = [
        "Hobbyist Programmer",
        "Backend Developer",
        "Bad Frontend Developer lol",
        "Furry",
        "Artist",
        "Canadian"
    ]

    if (!intro) setInterval(() => {
        index = ++index % titles.length
    }, 2000)
</script>

<div class:intro transition:fade>
    <div class:inner={intro}>
        <div class="mini">Hi, I'm</div>
        <div class="header orange">Malachi Hargreaves</div>
        <div class="mini">a</div>

        <div class="title orange">
            {#if intro}
                {titles[index]}
            {:else}
                {#key index}
                    <div in:fly={{ x: 50, delay: 250, duration: 250 }} out:fly={{ x: -50, duration: 250 }}>
                        {titles[index]}
                    </div>
                {/key}
            {/if}
        </div>
    </div>
</div>

<style>
    .intro {
        display: flex;

        justify-content: center;
        text-align: center;

        padding-top: 35vh;
        left: 50%;
        position: absolute;
    }

    .inner {
        left: -50%;
        position: relative;
    }

    .header {
        color: var(--fox-orange);
        font-size: 4rem;
        font-weight: 600;
    }

    .title {
        color: var(--fox-orange);
        padding-bottom: 50px;
        font-size: 3rem;
        max-height: 60px;
    }

    .mini {
        font-size: 2.5rem;
    }

    @media only screen and (max-width: 700px) {
        .header {
            font-size: 2rem;
            font-weight: 600;
        }

        .title {
            font-size: 1rem;
            max-height: 10px;
        }

        .mini {
            font-size: 1.25rem;
        }
    }
</style>
