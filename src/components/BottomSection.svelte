<script lang="ts">
    const items: any = [
        {
            title: 'How can I win?',
            content: 'Thanks to your membership, you also participate in our contest to win the iPhone15. We sellect a winner among every 600 participants. The next winner will be selected on 06.10.2023, and will be notified directly by e-mail. If the reward is out of stock, the winner will receive a similar product of equal or greater value instead.'
        },
        {
            title: 'No hidden fees?',
            content: 'We ensure that our members are provided with a detailed history of transactions so that they know exactly what they are paying for. Credit card information is only required to facilitate future purchases. There will be no charges on your credit card statement if you do not upgrade to PREMIUM membership and do not make a purchase.'
        },
        {
            title: 'Why do we need your billing information?',
            content: 'By joining this service, you will receive a 5-day trial of our partner\'s program. If you continue with a subscription beyond the 5-day trial period, you will be charged an amount on your credit card which varies depending on the choice of the tariff. When your contribution is deducted from your credit card or other payment method, you will have access to these services which are reserved exclusively for members of our partner\'s website.'
        }
    ]
</script>

{#if items.length > 0}
    <section class="bottom-section">
        {#each items as item}
            <div class="bottom-section__item">
                <strong class="bottom-section__item-title">{item.title}</strong>
                <p class="bottom-section__item-content">{item.content}</p>
            </div>
        {/each}
    </section>
{/if}

<style lang="scss">
  .bottom-section {
    background-color: var(--primary-background-color);
    display: grid;
    gap: 2rem;
    padding: 1.5rem 1rem;
    margin: 3rem -1rem 1rem;
    width: calc(100% + 2rem);

    @media (width > 35.5rem) {
      grid-template-columns: repeat(3, 1fr);
    }

    &__item-title {
      display: block;
      margin-bottom: 0.25rem;
      font-size: 1rem;
      line-height: 1.25rem;

      @media (width > 35.5rem) {
        font-size: 0.75rem;
      }
    }

    &__item-content {
      font-size: 0.875rem;
      line-height: 1rem;

      @media (width > 35.5rem) {
        font-size: 0.625rem;
      }
    }
  }
</style>