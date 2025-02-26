<template>
    <section class="scene" :id="scene">
        <div class="title-container">
            <slot></slot>
        </div>
    </section>
</template>

<script setup>
import { defineProps } from 'vue'

const props = defineProps({
    scene: String,
    viewport: Object,
})
</script>
