<script lang="ts">
    import {fade} from 'svelte/transition';
    import {onMount} from 'svelte';

    let photos = [
        'src/assets/slider_1.webp',
        'src/assets/slider_2.webp',
        'src/assets/slider_3.webp'
    ];
    let currentIndex = 0;

    const selectPhoto = (index: number) => {
        currentIndex = index;
    };

    onMount(() => {
        photos.forEach(photo => {
            const img = new Image();
            img.src = photo;
        });
    });
</script>

<style lang="scss">
  .slider-section {
    max-width: 480px;
    margin-inline: auto;
    margin-bottom: 2rem;

    @media (width > 768px) {
      width: 480px;
      max-width: 100%;
    }
  }

  .slider {
    position: relative;
    width: 100%;
    aspect-ratio: 1;
    overflow: hidden;
  }

  .photo {
    width: 100%;
    max-width: 100%;
    display: block;
    height: auto;
    max-height: 100%;
  }

  .thumbnails {
    margin-top: 1rem;
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
    justify-content: center;

    @media (width > 568px) {
      justify-content: space-between;
    }
  }

  .thumbnail {
    width: 72px;
    height: 72px;
    cursor: pointer;
    transition: transform 0.3s linear;
    border-radius: 20px;
    overflow: hidden;
    border: 1px solid var(--primary-color);

    @media (width> 568px) {
      width: 132px;
      height: 132px;
    }

    img {
      width: 100%;
      height: auto;
    }

    &:not(.active) img {
      opacity: 0.5;
    }
  }
</style>

<section class="slider-section">
    <div class="slider">
        {#each photos as photo, index (photo)}
            {#if index === currentIndex}
                <img src={photo} alt="Slider image {index}" class="photo" transition:fade>
            {/if}
        {/each}
    </div>
    <div class="thumbnails">
        {#each photos as photo, index}
            <button
                    type="button"
                    class="thumbnail {index === currentIndex ? 'active' : ''}"
                    on:click={(e) => {
                        e.preventDefault();
                        selectPhoto(index)
                    }}
            >
                <img src={photo} alt="Thumbnail"/>
            </button>
        {/each}
    </div>
</section>