<template>
  <Header :totalIncome="state.totalIncome" />
  <Form :state="state" @add-income="addIncome" />
  <IncomeList :state="state" @remove-item="removeItem"/>
</template>

<script setup>
import { reactive, computed } from 'vue'
import Header from './components/Header.vue'
import Form from './components/Form.vue'
import IncomeList from './components/IncomeList.vue';
const state = reactive({
  income: [],
  sortedIncome: computed(()=> {
    // eslint-disable-next-line vue/no-side-effects-in-computed-properties
    return state.income.sort((a, b) => {
      return b.date - a.date
    })
  }),
  totalIncome: computed(() => {
    let temp = 0
    if (state.income.length > 0) {
      for (let i = 0; i < state.income.length; i++) {
        temp += state.income[i].value
      }
    }
    return temp
  })
})
const addIncome = (obj) => {
    console.log(obj)
    let day = obj.date.split("-");
    let newDay = new Date(day[0], day[1], day[2])
    state.income = [...state.income, {
      id: Date.now(),
      desc: obj.desc,
      value: parseInt(obj.value),
      date: newDay.getTime()
    }]
    console.log(state.income)
}
const removeItem = (id) => {
  state.income = state.income.filter((item) => item.id!== id)
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Fira Sans', sans-serif;
}
body {
  background-color: #eee;
}
</style>
