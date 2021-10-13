<script lang="ts">
    type Detail = {
        service: string;
        description?: string;
    };

    const commissions: Detail[] = [
        {
            service: 'Rest APIs',
        },
        // {
        //     service: "Basic website",
        // },
        {
            service: 'Twitch Bot',
        },
        {
            service: 'Discord Bot',
            description: 'Guild bound discord bot or similar',
        },
    ];

    const info = [
        'I can make it happen',
        'but I am one person so I may not be able to create the next Facebook',
        'I can for a small project or similar.',
        'The things listed below are the only ones I will work on',
        "please don't ask for something not on this list",
        'I may decline any commission without reason.',
        'The price will be decided on the service and further details',
        'I will not do any work for free',
        'nor accept any gift items as payment',
        'The languages I use are JavaScript/TypeScript, Kotlin, Go and Python',
        "I may use what you prefer in that list or one I'm familiar with",
    ];

    const contact = [
        "You can contact me on my <a href='https://discord.gg/5dTpady' target='_blank'>Discord Server</a> or Telegram",
        'and we can discuss the details of said service',
        'please be reasonable and considerate',
        'thank you',
    ];
</script>

<div class="header">Have an idea you want created?</div>

{#if info.length}
    {#each info as item}
        <div class="text">{item}</div>
    {/each}
{/if}

<div class="title">What services do I offer?</div>

<table>
    {#each commissions as { service, description }}
        <tr>
            <td class="text">{service}</td>
            {#if description}
                <td class="text">{description}</td>
            {/if}
        </tr>
    {/each}
</table>

<div class="title">How do I contact and commission you?</div>

{#if contact.length}
    {#each contact as item}
        <div class="text">{@html item}</div>
    {/each}
{/if}

<style>
    .header {
        font-size: 2.5rem;
        font-weight: 500;
        padding-bottom: 50px;
    }

    .text {
        font-size: x-large;
        padding: 7px 0 7px 0;
    }

    .title {
        padding: 40px 0 20px 0;
        color: var(--fox-orange);
        font-size: xx-large;
    }

    :global(a) {
        color: var(--fox-orange);
        text-decoration: underline;
    }

    /* table */

    td.text {
        padding: 5px 15px;
    }

    table {
        border: 1px solid black;
        border-radius: 10px;
    }

    @media only screen and (max-width: 700px) {
        .header {
            font-size: x-large;
            padding-bottom: 20px;
        }

        .title {
            font-size: x-large;
            padding-top: 20px;
        }

        .text {
            font-size: large;
            padding: 5px 0 5px 0;
        }
    }
</style>
