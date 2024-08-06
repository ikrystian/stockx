<script>
    import Slider from "./components/Slider.svelte";
    import Form from "./components/Form.svelte";
    import Footer from "./components/Footer.svelte";
    import Articles from "./components/Articles.svelte";
    import BottomSection from "./components/BottomSection.svelte";
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

    <section class="title-section">
        <div class="container">
            <h2 class="title-section__heading">Top Tech Mystery Box<span> at Unbeatable Prices</span></h2>
            <p>Fast shipping | Easy returns | Special discounts for students</p>
        </div>
    </section>

    <Articles/>
    <BottomSection/>
</main>
<Footer/>