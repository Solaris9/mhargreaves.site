<script lang="ts">
    import { onDestroy } from 'svelte';
    // import { fade, fly } from 'svelte/transition';

    export let intro = true;

    let interval: number;
    let index = 0;
    let titles = ['Hobbyist Programmer', 'Backend Developer', 'Frontend Developer', 'Canadian'];

    if (!intro) {
        interval = setInterval(() => (index = ++index % titles.length), 2000);
        onDestroy(() => clearInterval(interval));
    }
</script>

<div class:intro>
    <div class:inner={intro}>
        <div class="mini">Hi, I'm</div>
        <div class="header orange">Malachi Hargreaves</div>
        <div class="mini">a</div>

        <div class="title orange">
            {#if intro}
                {titles[index]}
            {:else}
                {#key index}
                    <!-- <div
                        in:fly={{ x: 50, delay: 250, duration: 250 }}
                        out:fly={{ x: -50, duration: 250 }}>
                        {titles[index]}
                    </div> -->
                    <div>{titles[index]}</div>
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
        padding-bottom: 60px;
        font-size: 3rem;
        height: 70px;

        overflow: hidden;
    }

    .mini {
        font-size: 2.5rem;
    }

    @media only screen and (max-width: 700px) {
        .header {
            font-size: 1.75rem;
            font-weight: 600;
        }

        .title {
            font-size: 1.5rem;
            max-height: 10px;
        }

        .mini {
            font-size: 1.5rem;
        }
    }
</style>
