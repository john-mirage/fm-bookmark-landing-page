<script lang="ts">
    import BookmarkIcon from '@components/icon-bookmark.svelte'
    import IconButton from '@components/icon-button.svelte'
    import HamburgerIcon from '@components/icon-hamburger.svelte'
    import Navigation from '@components/navigation.svelte'
    import { onMount } from 'svelte';

    let topAppBarHasShadow = false
    function handleTopAppBarShadow() {
        if (!topAppBarHasShadow && window.scrollY > 0) {
            topAppBarHasShadow = true
        } else if (topAppBarHasShadow && window.scrollY <= 0) {
            topAppBarHasShadow = false
        }
    }

    onMount(() => {
        handleTopAppBarShadow()
    })
</script>

<svelte:window on:scroll={handleTopAppBarShadow} />

<template>
    <header
        class="top-app-bar"
        class:top-app-bar--shadow={topAppBarHasShadow}
    >
        <div class="top-app-bar__container">
            <a class="top-app-bar__logo" href="/">
                <BookmarkIcon />
            </a>

            <div class="top-app-bar__menu-button" on:click>
                <IconButton>
                    <HamburgerIcon />
                </IconButton>
            </div>

            <div class="top-app-bar__navigation">
                <Navigation onLight />
            </div>

            <button class="top-app-bar__login-button">Login</button>
        </div>
    </header>
</template>

<style lang="scss">
    @use '../assets/styles/variables';
    @use '../assets/styles/mixins';

    .top-app-bar {
        position: fixed;
        z-index: 100;
        top: 0;
        left: 0;
        display: flex;
        flex-direction: column;
        justify-content: flex-end;
        width: 100%;
        height: 8rem;
        background-color: variables.$color-white;

        @media screen and (min-width: variables.$screen-lg) {
            height: 10rem;
        }

        &--shadow {
            box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);
            height: auto;
        }

        &__container {
            @include mixins.container-2xl;
            display: flex;
            flex-direction: row;
            justify-content: flex-start;
            align-items: center;
            padding-top: 1rem;
            padding-bottom: 1rem;
        }

        &__logo {
            width: 14rem;

            @media screen and (min-width: variables.$screen-md) {
                width: 18rem;
            }
        }

        &__menu-button {
            width: auto;
            height: auto;
            margin-right: -1.2rem;
            margin-left: auto;

            @media screen and (min-width: variables.$screen-lg) {
                display: none;
            }
        }

        &__navigation {
            display: none;

            @media screen and (min-width: variables.$screen-lg) {
                display: block;
                margin-left: auto;
            }
        }

        &__login-button {
            display: none;

            @media screen and (min-width: variables.$screen-lg) {
                display: inline-block;
                padding: 1.6rem 4rem;
                border-radius: 0.6rem;
                background-color: variables.$color-soft-red;
                color: variables.$color-white;
                font-size: 1.4rem;
                font-weight: 500;
                text-transform: uppercase;
                letter-spacing: 0.2rem;
                margin-left: 6rem;
                transition-property: color, background-color;
                transition-duration: 150ms;

                &:hover {
                    background-color: transparent;
                    outline: 0.2rem solid variables.$color-soft-red;
                    color: variables.$color-soft-red;
                }
            }
        }
    }
</style>