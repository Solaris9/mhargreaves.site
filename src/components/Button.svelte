<script lang="ts" context="module">
    import { get, writable } from 'svelte/store';
    import { view } from '../App.svelte';

    export const buttons: Record<string, HTMLButtonElement> = {};
    export const current = writable<HTMLButtonElement>(null);

    export function set(name: string) {
        const button = buttons[name];
        if (!button) return;

        const active = get(current);
        current.set(button);

        if (active) active.disabled = false;
        button.disabled = true;

        view.set(name)

        window.location.hash = `#${name}`;
        document.title = `Malachi Hargreaves - ${name}`
    }
</script>

<script lang="ts">
    export let name: string;
</script>

<button bind:this={buttons[name]} on:click={() => set(name)}>
    <slot />
</button>

<style>    
    button {
        font-size: x-large;
        text-decoration: unset;

        border-radius: unset;
        border: unset;
        margin: unset;

        min-width: 175px;
        height: 100%;

        text-align: center;
        color: white;
        background-color: var(--dark-gray);

        transition: background-color .2s, color .2s;
    }

    button:hover:not(:disabled) {
        color: var(--fox-orange);
        cursor: pointer;
        
        transition: background-color color .2s;
    }

    button:disabled {
        background-color: var(--fox-orange);
        cursor: default;
    }

    @media only screen and (max-width: 600px) {
        button {
            font-size: x-small;
            text-decoration: unset;

            border-radius: unset;
            border: unset;
            margin: unset;

            text-align: center;
            justify-content: center;

            background-color: grey;
            color: unset;
        }
    }
</style>
