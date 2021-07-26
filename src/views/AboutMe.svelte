<script lang="ts">
    import Intro from '../components/Intro.svelte';

    const age = new Date().getFullYear() - new Date(2001, 5, 9).getFullYear();

    type Descriptions = { name?: String; list: string[] }[];

    const descriptions: Descriptions = [
        {
            list: [
                `I'm a ${age} year old living on Vancouver Island in British Columbia, Canada`,
                'I started this programming journey back around 2013 with Python and for some reason Batch',
                'Then I was mostly tinkering with text based games but being very basic',
                'In 2017 I found Node.JS and started to learn JavaScript, first with Discord.JS as bots were popular at the time',
                "Since then I've been learning new languages, libraries and frameworks",
                'Moving on to learning more Python, TypeScript, HTML, Java and then Kotlin which I mainly use (other than JS for obvious reason)',
                "I've also tried other languages such as Rust and the C languages C, C++ and C# but not getting much success from those",
                'Two careers I wish to be in is game development with C# and web development creating full fledge websites',
                'Along with the backend should either require.',
                'In all said, programming has been very fun and enjoyable to learn',
                'I plan to continue to expand my knowledge of it',
            ],
        },
        {
            name: "the site",
            list: [
                'I\'ll be honest, I\'ve used quite a few hacky solutions to make this site work',
                'you can find the source below on the footer'
            ],
        },
    ];
</script>

<Intro intro={false} />

{#each descriptions as { name, list }}
    {#if name}
        <div class="title">{name}</div>
    {/if}

    {#each list as item}
        <div class="text">{item}</div>
    {/each}
{/each}

<style>
    .text {
        font-size: x-large;
        padding: 7px 0 7px 0;
    }

    .title {
        padding: 40px 0 20px 0;
        color: var(--fox-orange);
        font-size: xx-large;
        font-size: 400;
    }

    @media only screen and (max-width: 700px) {
        .text {
            font-size: smaller;
        }

        .text {
            font-size: large;
        }
    }
</style>
