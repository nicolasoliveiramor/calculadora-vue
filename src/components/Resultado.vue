<script setup lang="ts">
import { defineProps } from 'vue'

const props = defineProps({
    resultado: {
        type: [Number, String],
        required: true
    }
})
</script>

<template>
    <div class="row">
        <div class="col-12 p-5 d-flex justify-content-center align-items-center">
            <h2>{{ props.resultado }}</h2>
        </div>
    </div>
</template>