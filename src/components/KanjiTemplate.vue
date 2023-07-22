<script setup></script>

<template>
    <div class="card">
        <p class="kanji">
            <slot name="kanji"></slot>
        </p>
        <p class="readings">
            <slot name="readings"></slot>
        </p>
        <p class="meanings">
            <slot name="meanings"></slot>
        </p>
    </div>
</template>

<style scoped lang="scss">
@use '../assets/base.css';
.card {
    background-color: rgb(50, 50, 50);
    border: .5em solid grey;
    color: white;
    width: 80%;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    text-align: center;
    border-radius: 1em;
    margin-top: 1em;
    box-shadow: var(--wrapper-box-shadow);
}

.kanji {
    font-size: 60pt;
    margin: .2em 0 0 0;
}

.readings {
    font-size: 32pt;
    margin: .1em 0;
}

.meanings {
    font-size: 30pt;
    margin: .1em 0;
}
</style>