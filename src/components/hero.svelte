<script lang="ts">
    import Container from '@components/container.svelte'
    import Button from '@components/button.svelte'
</script>

<div class="hero">
    <div class="hero__header">
        <img class="hero__illustration" src="src/assets/images/illustration-hero.svg" alt="Tablet illustration">
        <div class="hero__shape"></div>
    </div>

    <div class="hero__body">
        <Container>
            <h1 class="hero__title">A simple Bookmark Manager</h1>
            <p class="hero__subtitle">A clean and simple interface to organize your favourite websites. Open a new browser tab and see your sites load instantly. Try it for free.</p>
            <div class="hero__actions">
                <Button hero type="primary">Get it on Chrome</Button>
                <Button hero type="secondary">Get it on Firefox</Button>
            </div>
        </Container>
    </div>
</div>

<style>
    .hero {
        width: 100%;
        height: auto;
        padding-top: 5rem;
    }

    .hero__header {
        position: relative;
        width: 100%;
        height: auto;
        margin-bottom: 4rem;
    }

    .hero__illustration {
        position: relative;
        z-index: 20;
    }

    .hero__shape {
        position: absolute;
        z-index: 10;
        bottom: 0;
        right: 0;
        width: 80%;
        height: 80%;
        border-top-left-radius: 9999px;
        border-bottom-left-radius: 9999px;
        background-color: var(--color-soft-blue);
    }

    .hero__body {
        width: 100%;
        height: auto;
    }

    .hero__title {
        font-size: 3.2rem;
        font-weight: 500;
        color: var(--color-very-dark-blue);
        line-height: 4rem;
        text-align: center;
        margin-bottom: 2rem;
    }

    .hero__subtitle {
        font-size: 1.8rem;
        font-weight: 400;
        color: var(--color-grayish-blue);
        line-height: 3rem;
        text-align: center;
        margin-bottom: 4rem;
    }

    .hero__actions {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: flex-start;
    }
</style>