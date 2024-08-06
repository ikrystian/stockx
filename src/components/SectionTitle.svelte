<script>
    export let title = '';
    export let content = '';
</script>
<section class="title-section">
    <div class="container">
        <h2 class="title-section__heading">{ title}</h2>
        <p class="title-section__content">{ content }</p>
    </div>
</section>

<style lang="scss">
  .title-section {
    margin-block: 3rem 2rem;
    text-align: center;

    &__heading {
      font-size: 2rem;
      max-width: 49.375rem;
      margin-inline: auto;
      margin-bottom: 0.5rem;

      @media (width > 48rem) {
        font-size: 3rem;
        max-width: 30rem;
      }
    }

    &__content {
      font-size: 1rem;
      color: var(--primary-color);

      @media (width >  48rem) {
        font-size: 1.25rem;
        line-height: 1.5rem;
      }
    }
  }
</style>