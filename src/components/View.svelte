<script lang="ts" context="module">
    import { get, writable } from 'svelte/store';

    export const views: Record<string, HTMLElement> = {};
    export const current = writable<HTMLElement>(null);

    export function set(name: string) {
        const view = views[name];
        if (!view) return;

        const active = get(current);
        current.set(view);

        if (active) active.style.display = 'none';
        view.style.display = 'flex';
    }
</script>

<script lang="ts">
    export let name: string;
</script>

<div class="view" bind:this={views[name]} on:click={() => set(name)}>
    <slot />
</div>

<style>
    .view {
        display: none;
        margin: 75px 0 100px 50px;
        flex-direction: column;
    }

    @media only screen and (max-width: 700px) {
        .view {
            margin: 75px 0 0 -30px;
        }
    }
</style>
