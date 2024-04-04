<template>
    <div class="income-list">
        <IncomeItem v-for="item in state.sortedIncome" :key="item.id" :income="item" v-on:remove-item="removeItem"/>
    </div>
</template>

<script setup>
import IncomeItem from './IncomeItem.vue';

// eslint-disable-next-line no-unused-vars
const props = defineProps({
    state: Object
})
const emit = defineEmits(['remove-item'])
const removeItem = (id) => {
    emit('remove-item', id)
}
</script>

<style scoped>
.income-list {
    margin-top: 30px;
    padding: 15px;
}
</style>