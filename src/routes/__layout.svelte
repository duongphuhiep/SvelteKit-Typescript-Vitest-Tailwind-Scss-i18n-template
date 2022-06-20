<script context="module" lang="ts">
  import {
    register,
    init,
    getLocaleFromNavigator,
    isLoading,
  } from "svelte-i18n";

  register("en", () => import("../locales/en.json"));
  register("fr", () => import("../locales/fr.json"));
  register("vn", () => import("../locales/vn.json"));
  init({
    fallbackLocale: "en",
    initialLocale: getLocaleFromNavigator(),
  });

  import { waitLocale } from "svelte-i18n";

  export async function preload() {
    // awaits for the loading of the 'en-US' and 'en' dictionaries
    return waitLocale();
  }
</script>

<script lang="ts">
  import Header from "$lib/header/Header.svelte";
  import "../app.css";
  import { _ } from "svelte-i18n";
</script>

{#if $isLoading}
  Loading language, please wait..
{:else}
  <Header />

  <main>
    <slot />
  </main>

  <footer>
    <p>
      {$_("home")} visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to learn
      SvelteKit
    </p>
  </footer>
{/if}

<style>
  main {
    flex: 1;
    display: flex;
    flex-direction: column;
    padding: 1rem;
    width: 100%;
    max-width: 1024px;
    margin: 0 auto;
    box-sizing: border-box;
  }

  footer {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 40px;
  }

  footer a {
    font-weight: bold;
  }

  @media (min-width: 480px) {
    footer {
      padding: 40px 0;
    }
  }
</style>
