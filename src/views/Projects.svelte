<script lang="ts" context="module">
    import Icon from 'svelte-fa';
    import { faInfo } from '@fortawesome/free-solid-svg-icons';

    type Project = {
        name: string;
        image: string;
        collaborated?: string;
        description: string[];
        links: [display: string, link: string][];
    };

    const projects: Project[] = [];

    export const canDisplayProjects = () => projects.length > 0;
</script>

<div class="header">These are my active projects or projects I collaborate on</div>

{#each projects as { name, description, links, collaborated, image }}
    <div class="project">
        <div class="info">
            <img class="image" src={image} alt={name} />

            <div>
                <div class="name">{name}</div>

                <div class="links">
                    {#each links as [name, link], i}
                        <a class="link" target="_blank" href={link}>{name}</a>
                        {#if i != links.length - 1} • {/if}
                    {/each}
                </div>

                {#if collaborated}
                    <div class="text">
                        <Icon icon={faInfo} size="1x" color="var(--fox-orange)" style="padding-right: 10px" />
                        I work with <a target="_blank" href="https://github.com/{collaborated}">@{collaborated}</a> on
                        this project.
                    </div>
                {/if}
            </div>
        </div>

        <div class="quote">
            {#each description as text}
                <div class="text">{text}</div>
            {/each}
        </div>
    </div>
{/each}

<style>
    .image {
        width: 125px;
        height: 125px;
        border-radius: 20px;
        margin-right: 25px;
    }

    .info {
        display: flex;
        flex-direction: row;
        padding-bottom: 25px;
    }

    .name {
        font-size: 2rem;
        font-weight: 400;
    }

    .text {
        font-size: larger;
        padding: 7px 0 7px 0;
    }

    .header {
        font-size: 2.5rem;
        font-weight: 500;
        padding-bottom: 50px;
    }

    .project {
        padding: 25px 0 25px 0;
    }

    /* links */

    a {
        color: var(--fox-orange);
    }

    a:visited {
        color: none;
    }

    .links {
        padding-top: 10px;
        display: flex;
        flex-direction: row;
    }

    .link {
        font-size: larger;
    }

    .link:not(:last-child) {
        padding-right: 10px;
    }

    .link:not(:first-child) {
        padding-left: 10px;
    }

    /* other */

    .quote {
        content: none;
        border-left: solid 5px var(--fox-orange);
        padding: 0.5rem 0 0.5rem 1rem;
        margin-left: 10px;
    }

    @media only screen and (max-width: 700px) {
        .image {
            width: 85px;
            height: 85px;
            border-radius: 20px;
            margin-right: 15px;
        }

        .header {
            font-size: large;
            padding-bottom: 15px;
        }

        .name {
            font-size: 1.2rem;
            padding-bottom: unset;
        }

        .links {
            padding-top: unset;
        }

        .text,
        .link,
        .info .text {
            font-size: 1rem;
        }
    }
</style>
