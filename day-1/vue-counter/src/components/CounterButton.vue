<script setup>
    defineProps({
        action: {
            type: Function,
            required: true
        },
        label: {
            type: String,
            default: 'Кнопка'
        },
        color: {
            type: String,
            default: '#42b983'
        }
    })
</script>

<template>
    <button
        @click="action()"
        :style="{baclgroundColor: color}"
        class="btn"
    >
        {{ label }}
    </button>
</template>

<style scoped>
    .btn {
        margin: 0 5px;
        padding: 8px 15px;
        border: none;
        border-radius: 4px;
        cursor: pointer;
        transition: all 0.3s;
    }

    .btn:hover {
        opacity: 0.8;
        transform: translateY(-2px);
    }
</style>