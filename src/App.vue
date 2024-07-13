<template>
    <div id="app">
        <header>
            <h1 v-if="route.path === '/'">Услуги</h1>
            <h1 v-else="route.path === '/call-waiter'">Вызов<br />официанта</h1>
        </header>
        <main>
            <router-view></router-view>
        </main>
        <footer>
            <IconButton @click="$router.push('/')" :icon="HomeIcon" text="Главная" />
            <IconButton :icon="ListIcon" text="Вызов" disabled />
        </footer>
    </div>
</template>

<script setup>
import { RouterView } from 'vue-router';
import { useRoute } from 'vue-router';
import IconButton from './components/IconButton.vue';
import HomeIcon from './assets/home.svg';
import ListIcon from './assets/list.svg';
const route = useRoute();
</script>

<style lang="scss">
header {
    margin: 39px 15px 20px;
}

main {
    flex-grow: 1;
    margin: 0 15px;
}

h1 {
    text-align: center;
    font-family: 'Journal Sans New';
    font-size: 32px;
    font-style: normal;
    font-weight: 400;
    line-height: 39px;
    letter-spacing: 1.6px;
    text-transform: uppercase;
}

footer {
    display: flex;
    gap: 8px;
    height: 83px;
    padding: 15px;
    border-top: 1px solid rgba(244, 241, 237, 0.2);
}
</style>
