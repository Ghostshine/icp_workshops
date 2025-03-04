<script setup>
import { ref } from 'vue';
import { my_project_backend } from 'declarations/my_project_backend/index';
let greeting = ref('');

async function handleSubmit(e) {
  e.preventDefault();
  const target = e.target;
  const name = target.querySelector('#name').value;
  await my_project_backend.greet(name).then((response) => {
    greeting.value = response;
  });
}
</script>

<template>
  <main>
    <img src="/logo2.svg" alt="DFINITY logo" />
    <br />
    <br />
    <form action="#" @submit="handleSubmit">
      <label class="border-3 border-red-500" for="name">Enter your name: &nbsp;</label>
      <input id="name" alt="Name" type="text" class="border-1 border-red-500"/>
      <button type="submit" class="border-1 border-red-500">Confirm</button>
    </form>
    <section id="greeting">{{ greeting }}</section>
  </main>
</template>
