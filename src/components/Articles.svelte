<script lang="ts">
    // Define the interface for the image object
    interface Image {
        fileName: string;
        alt: string;
    }

    // Define the interface for the article object
    interface Article {
        title: string;
        content: string;
        image: Image;
    }

    // Define the articles array with the Article type
    const articles: Article[] = [
        {
            title: `Curious about the <strong style="color: var(--primary-color)">StockX</strong> Mystery Box?`,
            content: "<p>Experience the thrill of unboxing cutting-edge gadgets with Stockx Mystery Boxes. Each box is a treasure trove of high-quality electronics, handpicked to elevate your tech game.</p><p>Expect the unexpected! Our boxes are packed with the latest gadgets, from smartphones to gaming consoles, ensuring you get the best tech surprises every time.</p>",
            image: {
                fileName: "article-image-1.webp",
                alt: "article image"
            }
        },
        {
            title: "Why is everyone buzzing about these boxes?",
            content: "<p>Experience the thrill of unboxing cutting-edge gadgets with Stockx Mystery Boxes. Each box is a treasure trove of high-quality electronics, handpicked to elevate your tech game.</p><p>Expect the unexpected! Our boxes are packed with the latest gadgets, from smartphones to gaming consoles, ensuring you get the best tech surprises every time.</p>",
            image: {
                fileName: "article-image-2.webp",
                alt: "article image 2"
            }
        }
    ];
</script>

{#if articles.length > 0}
    <div class="container articles">
        {#each articles as article, index (article)}
            <article class="article" id="index-{index}">
                {#if article.image}
                    <div class="article__image-wrapper">
                        <img class="article__image" src="src/assets/{article.image.fileName}"
                             alt="Article image {index}">
                    </div>
                {/if}
                <div class="article__content-section">
                    <div>
                        {#if article.title}
                            <h3 class="article__title">{@html article.title}</h3>
                        {/if}
                        {#if article.content}
                            <div class="article__content">
                                {@html article.content}
                            </div>
                        {/if}
                    </div>
                </div>
            </article>
        {/each}
    </div>
{/if}

<style lang="scss">
  .article {
    display: flex;
    flex-direction: column;
    gap: 2rem;

    @media (width > 768px) {
      flex-direction: row;
      align-items: center;

      &:nth-child(even) {
        flex-direction: row-reverse;
      }
    }

    &:not(:last-child) {
      margin-bottom: 3rem;
    }

    &__image-wrapper {

      @media (width > 768px) {
        width: 250px;
      }

      @media (width > 992px) {
        width: 583px;
      }
    }

    &__content-section {
      flex: 1;
    }

    &__image {
      border-radius: 1.875rem;
      margin-inline: auto;
    }

    &__title {
      font-size: 1.5rem;
      line-height: 1;
      font-weight: 700;
      margin-bottom: 1rem;

      @media (width > 768px) {
        font-size: 2.625rem;
        line-height: 3.25rem;
        margin-bottom: 1.5rem;
      }
    }
  }
</style>