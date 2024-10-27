<script setup lang="ts">
import { defineEmits, defineProps } from 'vue';

const emit = defineEmits();
const props = defineProps({
    valor1: Number,
    valor2: Number,
    operador: String,
});
</script>

<template>
    <div class="row">
        <div class="col-12 gap-4 p-5 d-flex justify-content-center">
            <input :value="props.valor1" @input="emit('update:valor1', +($event.target as HTMLInputElement).value)"
                class="form-control-sm" type="number" placeholder="Valor 1" />
            <select :value="props.operador"
                @change="emit('update:operador', ($event.target as HTMLSelectElement).value)" class="form-select-sm">
                <option value="+">+</option>
                <option value="-">-</option>
                <option value="*">x</option>
                <option value="/">÷</option>
            </select>
            <input :value="props.valor2" @input="emit('update:valor2', +($event.target as HTMLInputElement).value)"
                class="form-control-sm" type="number" placeholder="Valor 2" />
        </div>
    </div>
</template>

<style lang="scss" scoped>
@import "@/styles/custom-bootstrap.scss";

div {
    background-color: $background-principal;
}
</style>
