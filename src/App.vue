<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>
    <div class="wrapper">
      <nav>     
        <div class="routerlink">
          <RouterLink to="/">Home</RouterLink>
        </div>
        <div class="routerlink">
          <RouterLink to="/about">About</RouterLink>
        </div>
        <div class="routerlink">          
          <RouterLink to="/todo">Todo</RouterLink>
        </div>
        <div class="routerlink">
          <RouterLink to="/kanji">Kanji</RouterLink>
        </div>
        <div class="routerlink">
          <RouterLink to="/shorturl">URL</RouterLink>
        </div>
      </nav>
    </div>
  </header>
  <main>
    <HelloWorld />
    <RouterView />
  </main>
</template>

<style lang="scss">
@use './assets/base.css';
nav {
  background-color: var(--color-background-mute);
  border-bottom: .3em solid var(--color-border);
  padding-top: 2em;

  a {
    color: var(--color-link);
    text-decoration: none;
    padding: 0 .3em;
    font-size: 16pt;
    padding: .3em;
    transition: 0.3s;
  }

  .routerlink {
    display: inline-block;
    transition: 0.3s;

    :focus {
      background-color: var(--color-border);
      border-radius: .3em .3em 0 0;
    }
  }
  .router-link-active {
    background-color: var(--color-border);
    border-radius: .3em .3em 0 0;
    padding: .15em;
  }

  @media (hover: hover) {
    a:hover {
      filter: brightness(60%);
      text-decoration: underline;
    }

    .routerlink:hover {
      background-color: var(--color-border);
      border-radius: .3em .3em 0 0;
    }
  }
}
</style>
