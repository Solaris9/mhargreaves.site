<script lang="ts">
    type CommissionDetail = {
        service: string;
        description?: string;
        examples?: string[];
    };

    const commissions: CommissionDetail[] = [
        {
            service: 'Rest APIs',
        },
        {
            service: "Basic website",
            examples: [ 'https://mhargreaves.site' ],
            description: 'Must have designs and references',
        },
        {
            service: 'Twitch Bot',
            description: 'Channel bound bot or similar',
        },
        {
            service: 'Discord Bot',
            description: 'Guild bound discord bot or similar',
        },
    ];

    const info = [
        'The things listed below are the only ones I will work on',
        "please don't ask for something not on this list",
        'I may decline any commission without reason.',
        'The price will be decided on the service and further details',
        'I will not do any work for free nor accept any gift items as payment',
        'The languages I use are JavaScript/TypeScript, Kotlin, Go and Python',
        "I may use what you prefer in that list or one I'm familiar with",
    ];

    const link = (url: string, text: string) => `<a href='http://${url}' target='_blank'>${text}</a>`

    const contact = [
        `You can contact me on my ${link('discord.gg/5dTpady', 'Discord Server')} or ${link('t.me/SolarisFox', 'Telegram')}`,
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

<div class="title">Do you have any examples?</div>

<table>
    {#each commissions as { service, examples }}
        {#if examples?.length}
        <tr>
            <td class="text">{service}</td>
            <td class="text examples">
                {#each examples as example}
                    <a href={example} target='_blank'>{example}</a>
                {/each}
            </td>
            </tr>
        {/if}
    {/each}
</table>

<section>
    <div class="title">How do I pay you?</div>
    <div class="text">I accept payment through PayPal, currency is in Canadian Dollars (CAD)</div>
</section>

<div class="title">How do I contact you?</div>

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
        padding: 5px 0 5px 0;
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

    .examples {
        display: flex;
        flex-direction: row;
        gap: 10px;
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
