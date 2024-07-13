<script setup>
import { ref } from 'vue';
import axios from 'axios';
import Button from './Button.vue';

const formData = ref({
    name: '',
    phone: '',
    location: '',
    comment: '',
});

async function submitForm(formData) {
    const targetUrl = 'https://webhook.site/994c8d78-82a5-4981-bc1a-3f00cfea293f';

    try {
        await axios.post(targetUrl, formData, {
            headers: {
                Accept: 'application/json',
                'Content-Type': 'application/json',
            },
        });
    } catch (error) {
        console.error(error);
    }
}
</script>

<template>
    <form @submit.prevent="submitForm">
        <p>
            <label for="name">Имя</label>
            <input
                v-model="formData.name"
                placeholder="Константинов Константин"
                type="text"
                name="name"
                id="name"
                required />
        </p>

        <p>
            <label for="phone">Телефон</label>
            <input
                v-model="formData.phone"
                placeholder="+7 (...) ... - .. - .."
                type="tel"
                name="phone"
                id="phone"
                required />
        </p>

        <p>
            <label for="location">Локация</label>

            <input
                v-model="formData.location"
                placeholder="Piazetta"
                type="text"
                name="location"
                id="location"
                required />
        </p>
        <p>
            <label for="comment">Комментарий</label>

            <textarea
                v-model="formData.comment"
                placeholder="Введите текст сообщения..."
                type="text"
                name="comment"
                id="comment"
                required></textarea>
        </p>

        <Button type="submit" text="Вызвать" color="#E7BDA6" />
    </form>
</template>

<style lang="scss" scoped>
form {
    display: flex;
    flex-direction: column;
    gap: 16px;
    margin: 20px 0;

    p {
        display: flex;
        flex-direction: column;
        gap: 8px;
        padding-bottom: 12px;
        border-bottom: 1px solid rgba(244, 241, 237, 0.2);

        label {
            text-align: left;
            color: var(--white, #f4f1ed);
            font-family: 'Journal Sans New';
            font-size: 16px;
            font-style: normal;
            font-weight: 400;
            line-height: 24px;
            opacity: 0.6;
        }

        input,
        textarea {
            resize: none;
            background-color: transparent;
            border: none;
            color: var(--white, #f4f1ed);
            text-align: left;
            font-family: 'Journal Sans New';
            font-size: 18px;
            font-style: normal;
            font-weight: 400;
            line-height: 25px;

            &:focus {
                outline: none;
                border: none;
            }

            &::placeholder {
                color: var(--white, #f4f1ed);
                opacity: 0.6;
            }
        }
    }
}
</style>
