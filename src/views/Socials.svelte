<script lang="ts">
    import Icon from 'svelte-fa';
    import {
        faYoutube,
        faSteam,
        faTelegram,
        faDiscord,
        faGithub,
        faInstagram,
        faTwitch,
    } from '@fortawesome/free-brands-svg-icons';
    import type { IconDefinition } from '@fortawesome/fontawesome-common-types';

    const socials: [name: string, icon: IconDefinition, url: string | null][] = [
        ['Solaris9', faGithub, 'github.com/Solaris9'],
        ['Solaris#1969', faDiscord, null],
        ['SolarisFox', faTelegram, 't.me/SolarisFox'],
        ['SolarisTheFox', faSteam, 'steamcommunity.com/id/SolarisTheFox'],
        ['solaris_fox', faTwitch, 'twitch.com/solaris_fox'],
        ['Solaris', faYoutube, 'youtube.com/channel/UCB1aY-6pvwkqvBl4-nHu4sQ'],
        // ['solaris_the_fox', faInstagram, 'instagram.com/solaris_the_fox/'],
    ];
</script>

<div class="header">Hey! Want to check me out on other platforms? Find them here!</div>

<div class="socials">
    {#each socials as [name, icon, url]}
        <div class="social">
            {#if url}
                <a href="https://{url}" target="_blank">
                    <div class="icon">
                        <Icon {icon} size="6x" />
                    </div>
                    <div class="name">@{name}</div>
                </a>
            {:else}
                <div class="icon">
                    <Icon {icon} size="6x" />
                </div>
                <div class="name">@{name}</div>
            {/if}
        </div>
    {/each}
</div>

<style>
    .header {
        font-size: 2.5rem;
        font-weight: 500;
        padding-bottom: 75px;
    }

    .name {
        font-size: 1.25rem;
        font-weight: 500;
        padding-bottom: 20px;
    }

    .socials {
        display: flex;
        flex-wrap: wrap;
        flex-grow: 1;
    }

    .social {
        display: flex;

        width: 170px;
        padding-bottom: 20px;

        justify-content: center;
        flex-direction: column;
        text-align: center;
    }

    .icon {
        padding-bottom: 15px;
    }

    a,
    a:visited {
        color: unset;
        transition: color 0.2s ease;
        text-decoration: none;
    }

    a:hover {
        color: var(--fox-orange);
        transition: color 0.2s ease;
    }

    @media only screen and (max-width: 700px) {
        .header {
            font-size: x-large;
            padding-bottom: 20px;
        }
        
        .name {
            font-size: large;
            padding: 5px 0 5px 0;
        }

        .socials {
            justify-content: center;
        }

        .social {
            width: 150px;
        }
    }
</style>
