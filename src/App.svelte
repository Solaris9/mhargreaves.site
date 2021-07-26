<script lang="ts">
    import { onMount } from 'svelte';
    import { fade } from 'svelte/transition';

    import Icon from 'svelte-fa';
    import { faBars } from '@fortawesome/free-solid-svg-icons';

    import Button, { buttons, set as setButton } from './components/Button.svelte';
    import View, { set as setView } from './components/View.svelte';

    import AboutMe from './views/AboutMe.svelte';
    import Projects from './views/Projects.svelte';
    import Commissions from './views/Commissions.svelte';
    import Socials from './views/Socials.svelte';
    import Contact from './views/Contact.svelte';
    import Intro from './components/Intro.svelte';

    let shouldShow = true;
    let div: HTMLElement;
    let footer: HTMLElement;

    onMount(() => {
        setTimeout(() => (shouldShow = false), 1500);
        setTimeout(() => {
            const name = window.location.hash.slice(1) || 'aboutme';

            if (name in buttons) {
                setButton(name);
                setView(name);
            }
        }, 2000);
    });

    function openButtons() {
        div.style.display = div.style.display == 'flex' ? 'none' : 'flex';
    }
</script>

{#if shouldShow}
    <Intro />
{:else}
    <div class="main" transition:fade={{ delay: 500 }}>
        <button class="toggle" on:click={openButtons}>
            <Icon icon={faBars} size="2x" />
        </button>

        <div bind:this={div} class="buttons">
            <Button name="aboutme">about me</Button>
            <Button name="projects">projects</Button>
            <Button name="commissions">commissions</Button>
            <Button name="socials">socials</Button>
            <Button name="contact">contact</Button>
        </div>

        <div class="content">
            <View name="aboutme"><AboutMe /></View>
            <View name="projects"><Projects /></View>
            <View name="commissions"><Commissions /></View>
            <View name="socials"><Socials /></View>
            <View name="contact"><Contact /></View>
        </div>
    </div>

    <footer bind:this={footer} transition:fade={{ delay: 500 }}>Created by Solaris9 (Malachi Hargreaves) • <a href="https://github.com/Solaris9/mhargreaves.site">source on github.com</a></footer>
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
        font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;
        color: white;
    }

    :global(input, button, select, textarea) {
        font-family: inherit;
        font-size: inherit;
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
        justify-items: stretch;

        height: 100vh;
    }

    .content {
        margin-left: 175px;
    }

    .toggle {
        display: none;
    }

    @media only screen and (max-width: 700px) {
        .buttons {
            display: none;
        }

        .toggle {
            display: block;
            z-index: 50;
            margin: 10px 0 0 10px;
            max-height: 42px;

            background-color: unset;

            border-radius: 7px;
            border: 2px solid black;
            box-shadow: 2px 2px 2px grey;
        }

        .content {
            margin: unset;
        }

        :global(body) {
            margin-right: 15px;
        }
    }

    footer {
        font-size: larger;
        text-align: center;
        height: 50px;
    }

    a {
        color:var(--fox-orange);
        text-decoration: none;
    }
</style>
