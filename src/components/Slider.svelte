<script lang="ts">
    import { fade } from 'svelte/transition';
    import { onMount } from 'svelte';

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

<style>
    .slider {
        position: relative;
        width: 100%;
        height: 300px;
        max-width: 800px;
        margin: auto;
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
        display: flex;
        justify-content: center;
        margin-top: 10px;
    }
    .thumbnail {
        width: 60px;
        height: 60px;
        margin: 0 5px;
        cursor: pointer;
        transition: transform 0.3s ease;
    }
    .thumbnail:hover {
        transform: scale(1.1);
    }
    .thumbnail img {
        width: 100%;
        height: auto;
        border: 2px solid transparent;
    }
    .thumbnail.active img {
        border-color: #333;
    }
</style>

<div class="slider">
    {#each photos as photo, index (photo)}
        {#if index === currentIndex}
            <img src={photo} alt="Photo" class="photo" transition:fade />
        {/if}
    {/each}
</div>
<div class="thumbnails">
    {#each photos as photo, index}
        <div
                class="thumbnail {index === currentIndex ? 'active' : ''}"
                on:click={() => selectPhoto(index)}
        >
            <img src={photo} alt="Thumbnail" />
        </div>
    {/each}
</div>
