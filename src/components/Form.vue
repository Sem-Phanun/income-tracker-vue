<!-- eslint-disable vue/multi-word-component-names -->
// eslint-disable-next-line vue/multi-word-component-names

<template>
  <form @submit.prevent="handleForm">
    <input type="text" placeholder="description" v-model="formData.desc" />
    <input type="number" placeholder="number" v-model="formData.value"/>
    <input type="date" placeholder="date" v-model="formData.date"/>
    <input type="submit" value="submit" />
  </form>
</template>

<script setup>

import { reactive } from 'vue';
// eslint-disable-next-line no-unused-vars
const props = defineProps({
    state: Object
})
// eslint-disable-next-line no-unused-vars
const { emit } = defineEmits(['event'])
const formData = reactive ({
    desc: null,
    value: null,
    date: null
})
const handleForm = () => {
    // emit('event', formData)
    console.log(formData)
}
handleForm()
</script>

<style scoped>
form {
  display: flex;
  justify-content: center;
  margin-top: 30px;
}

form input {
  color: #888;
  border: none;
  outline: none;
  font-size: 20px;
}

form input::placeholder {
  color: #aaa;
}

form input:not([type='submit']) {
  display: block;
  background: #fff;
  border: none;
  outline: none;
  padding: 5px 15px;
}

form input[type='submit'] {
  display: block;
  border: none;
  background: none;
  outline: none;

  color: #fff;
  font-weight: 500;
  text-shadow: 0px 1px 3px rgba(0, 0, 0, 0.2);
  padding: 5px 15px;
  background-color: #ffce00;

  cursor: pointer;
}

form input:first-of-type {
  border-radius: 8px 0px 0px 8px;
}

form input:last-of-type {
  border-radius: 0px 8px 8px 0px;
}
</style>
