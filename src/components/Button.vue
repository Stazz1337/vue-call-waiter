<template>
    <button
        @click="$emit('click')"
        :disabled="disabled"
        :style="{ 'background-color': color }"
        :type="type">
        <p>{{ text }}</p>
    </button>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';
defineProps({
    text: String,
    color: String,
    type: String,
    disabled: Boolean,
});

defineEmits(['click']);
</script>

<style lang="scss" scoped>
button {
    display: flex;
    align-items: center;
    justify-content: center;
    border: none;
    width: 100%;
    min-height: 60px;
    border-radius: 12px;
    background: var(--white, #f4f1ed);

    &:hover {
        cursor: pointer;
        opacity: 0.8;
    }

    p {
        color: #415263;

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
    }
}
</style>
