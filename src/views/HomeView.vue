<script setup lang="ts">
import TheWelcome from '../components/TheWelcome.vue'
import {onMounted, ref} from "vue";
import axios from "axios";

const myVar = ref<String>("");

onMounted(() => {
  axios.get("/hello").then(response => {
    console.log(response.data);
    myVar.value = response.data;
  });
});
</script>

<template>
  <main>
    <h1>{{myVar}}!</h1>
    <TheWelcome />
  </main>
</template>
