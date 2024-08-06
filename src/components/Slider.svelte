<script lang="ts">
    import {fade} from 'svelte/transition';
    import {onMount} from 'svelte';

    // Define the type for a photo object
    interface Photo {
        src: string;
        new_price: number;
        old_price: number;
    }

    // Define the photos array with the Photo type
    let photos: Photo[] = [
        {src: '/assets/slider_1.webp', new_price: 1.99, old_price: 500},
        {src: '/assets/slider_2.webp', new_price: 1.98, old_price: 501},
        {src: '/assets/slider_3.webp', new_price: 1.07, old_price: 502},
    ];

    // Define the currentIndex with a number type
    let currentIndex: number = 0;

    // Add a type annotation for the index parameter
    const selectPhoto = (index: number): void => {
        currentIndex = index;
    };

    // Use the Photo type in the forEach callback
    onMount(() => {
        photos.forEach((photo: Photo) => {
            const img = new Image();
            img.src = photo.src;
        });
    });
</script>

<section class="slider__section">
    <div class="slider__container">
        {#each photos as photo, index (photo.src)}
            {#if index === currentIndex}
                <div transition:fade>
                    <div class="slider__promo">
                        <strong class="slider__promo-price">${photo.new_price}</strong>
                        <p class="slider__promo-description">Original value <span>${photo.old_price}</span></p>
                    </div>
                    <img src={photo.src} alt="Slider image {index}" class="slider__photo">
                </div>
            {/if}
        {/each}
    </div>
    <div class="slider__thumbnails">
        {#each photos as photo, index}
            <button
                    type="button"
                    class="slider__thumbnail {index !== currentIndex ? 'slider__thumbnail--inactive' : ''}"
                    on:click={(e) => {
                        e.preventDefault();
                        selectPhoto(index)
                    }}
            >
                <img loading="lazy" src={photo.src} alt="Thumbnail {index}" class="slider__thumbnail-img"/>
            </button>
        {/each}
    </div>
</section>


<style lang="scss">
  .slider {
    &__section {
      max-width: 30rem; // 480px / 16 = 30rem
      margin-inline: auto;
      margin-bottom: 2rem;

      @media (width > 48rem) { // 768px / 16 = 48rem
        width: 30rem; // 480px / 16 = 30rem
        max-width: 100%;
      }
    }

    &__container {
      position: relative;
      width: 100%;
      aspect-ratio: 1;
      overflow: hidden;
    }

    &__promo {
      background-color: var(--primary-color);
      color: var(--invert-text);
      width: 10rem; // 160px / 16 = 10rem
      height: 10rem; // 160px / 16 = 10rem
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      gap: 0.5rem;
      border-radius: 50%;
      position: absolute;
      top: 0.625rem;
      right: 0.625rem;
      box-shadow: 0 0 0 0 rgba(0, 0, 0, 1);
      transform: scale(1);
      animation: pulse 2s infinite;

      &-price {
        font-size: 2rem;
        font-weight: 700;
        line-height: 2.75rem;
      }

      &-description {
        font-weight: 400;
        font-size: 0.875rem;
        line-height: 1rem;
      }
    }

    &__photo {
      width: 100%;
      max-width: 100%;
      display: block;
      height: auto;
      max-height: 100%;
    }

    &__thumbnails {
      margin-top: 1rem;
      display: flex;
      gap: 0.5rem;
      flex-wrap: wrap;
      justify-content: center;

      @media (width > 35.5rem) { // 568px / 16 = 35.5rem
        justify-content: space-between;
      }
    }

    &__thumbnail {
      width: 4.5rem; // 72px / 16 = 4.5rem
      height: 4.5rem; // 72px / 16 = 4.5rem
      cursor: pointer;
      transition: transform 0.3s linear;
      border-radius: 1.25rem; // 20px / 16 = 1.25rem
      overflow: hidden;
      border: 0.0625rem solid var(--primary-color); // 1px / 16 = 0.0625rem

      @media (width > 35.5rem) { // 568px / 16 = 35.5rem
        width: 8.25rem; // 132px / 16 = 8.25rem
        height: 8.25rem; // 132px / 16 = 8.25rem
      }

      &-img {
        width: 100%;
        height: auto;
      }

      &--inactive &-img {
        opacity: 0.5;
      }
    }
  }
</style>
