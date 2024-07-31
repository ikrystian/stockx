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


    <section class="bottom-section">
        <div class="bottom-section__item">
            <strong>How can I win?</strong>
            <p>Thanks to your membership, you also participate in our contest to win the iPhone15. We sellect a winner among every 600 participants. The next winner will be selected on 06.10.2023, and will be notified directly by e-mail. If the reward is out of stock, the winner will receive a similar product of equal or greater value instead.</p>
        </div>

        <div class="bottom-section__item">
            <strong>No hidden fees?</strong>
            <p>We ensure that our members are provided with a detailed history of transactions so that they know exactly what they are paying for. Credit card information is only required to facilitate future purchases. There will be no charges on your credit card statement if you do not upgrade to PREMIUM membership and do not make a purchase.</p>
        </div>

        <div class="bottom-section__item">
            <strong>Why do we need your billing information?</strong>
            <p>By joining this service, you will receive a 5-day trial of our partner's program. If you continue with a subscription beyond the 5-day trial period, you will be charged an amount on your credit card which varies depending on the choice of the tariff. When your contribution is deducted from your credit card or other payment method, you will have access to these services which are reserved exclusively for members of our partner's website.</p>
        </div>

    </section>

</main>
<footer class="footer">
    credit cards
</footer>