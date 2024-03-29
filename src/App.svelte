<script lang="ts" context="module">
    import type { SvelteComponent } from 'svelte';
    import { writable } from 'svelte/store';
    import Button, { buttons, set } from './components/Button.svelte';

    import AboutMe from './views/AboutMe.svelte';
    import Projects, { canDisplayProjects } from './views/Projects.svelte';
    import Commissions from './views/Commissions.svelte';
    import Socials from './views/Socials.svelte';

    export const view = writable<string>(null);

    const views: Record<string, typeof SvelteComponent> = {
        'about me': AboutMe,
        commissions: Commissions,
        socials: Socials,
    };

    if (canDisplayProjects()) views["projects"] = Projects;
</script>

<script lang="ts">
    import { onMount } from 'svelte';
    import { fade, fly } from 'svelte/transition';

    import Intro from './components/Intro.svelte';

    let showIntro = true;
    let showSite = false;

    onMount(() => {
        setTimeout(() => (showIntro = false), 1500);
        setTimeout(() => (showSite = true), 2000);
        setTimeout(() => {
            let name = window.location.hash.slice(1);
            if (!(name in buttons)) name = 'about me';

            set(name);
        }, 2000);
    });
</script>

{#if showIntro}
    <Intro />
{/if}

{#if showSite}
    <div class="main" transition:fade>
        <div class="buttons">
            {#each Object.keys(views) as name}
                <Button {name}>{name}</Button>
            {/each}
        </div>

        <div class="content">
            {#key $view}
                <div class="view"
                    in:fly={{ x: 50, duration: 150, delay: 150 }}
                    out:fly={{ x: 50, duration: 150 }}>
                    <svelte:component this={views[$view]} />
                </div>
            {/key}
        </div>
    </div>

    <footer transition:fade>
        created by Solaris9 • <a href="https://github.com/Solaris9/mhargreaves.site" target="_blank">source</a>
    </footer>
{/if}

<style>
    /* variables */
    :global(:root) {
        --fox-orange: #ff652f;
        --dark-gray: #1f2833;
        --darker-gray: #0b0c10;
    }

    /* site */

    :global(body) {
        background-color: var(--darker-gray);
        height: 100%;
        margin: 0;
        font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell,
            'Helvetica Neue', sans-serif;
        color: white;
    }

    /* main  */

    .main {
        display: flex;
        min-height: calc(100vh - 50px);
    }

    .buttons {
        display: flex;
        position: fixed;

        flex-direction: column;
        justify-content: space-between;

        height: 100vh;
    }

    .content {
        margin-left: 175px;
    }

    .view {
        margin: 75px 50px 80px 50px;
    }

    @media only screen and (max-width: 1080px) {
        .view {
            margin: 125px 0 0 -30px;
        }

        .buttons {
            width: 100%;
            max-width: 100vw;
            flex-direction: row;
            height: 50px;
        }

        .content {
            margin: -50px 0 0 50px;
        }

        :global(body) {
            margin-right: 15px;
        }

        footer {
            padding-left: unset !important;
            font-size: 1px;
            text-align: center;
            height: 50px;
            padding-top: 20px;
        }
    }

    footer {
        padding-left: 175px;
        font-size: larger;
        text-align: center;
        height: 50px;
    }

    a {
        color: var(--fox-orange);
        text-decoration: none;
    }
</style>
