<script setup>
import Button from './Button.vue';
</script>

<template>
    <div class="home">
        <Button @click="$router.push('/call-waiter')" type="button" text="Вызвать официанта" />
    </div>
</template>
