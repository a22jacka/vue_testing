<script setup lang="ts">
import KanjiTemplate from './KanjiTemplate.vue'
</script>

<template>
    <KanjiTemplate>
        <template #kanji>
            何
        </template>

        <template #readings>
            なに、なん
        </template>

        <template #meanings>
            <div class="m_list">
                <ol>
                    <li>what</li>
                </ol>
            </div>
        </template>
    </KanjiTemplate>
    <KanjiTemplate>
        <template #kanji>
            愛
        </template>
        <template #readings>
            あい、なま
        </template>
        <template #meanings>
            <div class="m_list">
                <ol>
                    <li>love, affection</li>
                </ol>
            </div>       
        </template>
    </KanjiTemplate>
    <KanjiTemplate>
        <template #kanji>
            犬
        </template>
        <template #readings>
            いぬ、いぬはし
        </template>
        <template #meanings>
            <div class="m_list">
                <ol>
                    <li>dog</li>
                    <li>snitch, spy</li>
                    <li>loser</li>
                    <li>counterfit, inferior</li>
                </ol>
            </div>
        </template>
    </KanjiTemplate>
    <KanjiTemplate>
        <template #kanji>
            大
        </template>
        <template #readings>
            おお、だい、たい、おおき
        </template>
        <template #meanings>
            <div class="m_list">
                <ol>
                    <li>large, big</li>
                    <li>great, prominent</li>
                    <li>older, senior</li>
                </ol>
            </div>
        </template>
    </KanjiTemplate>
</template>

<style scoped>
.m_list {
    width: fit-content;
    margin: 0 auto;
}
</style>