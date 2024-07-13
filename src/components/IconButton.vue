<template>
    <button @click="$emit('click')" type="button" :disabled="disabled">
        <img :src="icon" alt="иконка" />
        <p>{{ text }}</p>
    </button>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';
defineProps({
    icon: String,
    text: String,
    disabled: Boolean,
});

defineEmits(['click']);
</script>

<style lang="scss" scoped>
button {
    display: flex;
    gap: 4px;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    border: none;
    background-color: transparent;
    width: 100%;

    &:hover {
        cursor: pointer;
        opacity: 0.8;
    }

    img {
        width: 24px;
        height: 24px;
        object-fit: cover;
    }

    p {
        height: 25px;
        color: var(--Gold, #e7bda6);
        text-align: center;
        font-family: 'Journal Sans New';
        font-size: 18px;
        font-style: normal;
        font-weight: 400;
        line-height: 25px;
    }

    &:disabled {
        cursor: not-allowed;
        opacity: 1;
        p {
            color: #f4f1ed;
        }
    }
}
</style>
