<script>
    import Slider from "./components/Slider.svelte";
    import Form from "./components/Form.svelte";
    import articleImage from "./assets/article-image.svg";
</script>

<main>
    <div class="container main-container">
        <div class="row">
            <div class="col">
                <Slider/>
            </div>
            <div class="col form-col">
                <h1>Chance to win a StockX Mystery Box today!</h1>
                <p>Unleash the Excitement of Mystery Electronics</p>
                <Form/>
            </div>
        </div>
    </div>

    <div class="container">
        <h2 class="title">Top Tech Mystery Box at Unbeatable Prices</h2>
        <p>Fast shipping | Easy returns | Special discounts for students</p>
    </div>

    <div class="container articles">
        <article class="article">
            <div class="article__image-section">
                <img src={articleImage} alt="article image">
            </div>
            <div class="article__content-section">
                <div>
                    <h3 class="article__title">Curious about the <strong>StockX</strong> Mystery Box?</h3>
                    <p>Experience the thrill of unboxing cutting-edge gadgets with Stockx Mystery Boxes. Each box is a
                        treasure trove of high-quality electronics, handpicked to elevate your tech game.</p>
                    <p>Expect the unexpected! Our boxes are packed with the latest gadgets, from smartphones to gaming
                        consoles, ensuring you get the best tech surprises every time.</p>
                </div>
            </div>
        </article>
        <article class="article">
            <div class="article__image-section">
                <img src={articleImage} alt="article image">
            </div>
            <div class="article__content-section">
                <div>
                    <h3 class="article__title">Curious about the StockX Mystery Box?</h3>
                    <p>Experience the thrill of unboxing cutting-edge gadgets with Stockx Mystery Boxes. Each box is a
                        treasure trove of high-quality electronics, handpicked to elevate your tech game.</p>
                    <p>Expect the unexpected! Our boxes are packed with the latest gadgets, from smartphones to gaming
                        consoles, ensuring you get the best tech surprises every time.</p>
                </div>
            </div>
        </article>
    </div>


    <div class="bottom-section">
        Bottom section
    </div>

</main>
<footer class="footer">
    credit cards
</footer>