<script setup lang="ts">
import TheWelcome from '../components/TheWelcome.vue'
import {onMounted, ref} from "vue";
import axios from "axios";

const people = ref<Person[]>([]);

interface Person {
  id: number;
  firstName: string;
  lastName: string;
}

onMounted(() => {
  axios.get<Person[]>("/hello").then(response => {
    people.value = response.data;
  });
});
</script>

<template>
  <main>
    <TheWelcome />
    <ul>
      <li v-for="person in people">{{ person.firstName }} {{ person.lastName }}</li>
    </ul>
  </main>
</template>
