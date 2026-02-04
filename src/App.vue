<script setup>

import { ref } from 'vue';
import Tabs from './Components/Tabs.vue';
import ToDo from './Pages/ToDo.vue';
import Modals from './Pages/Modals.vue';
let titles = ref([
  'Todo',
  'Modals'

]);
let contents = ref([
  ToDo,
  Modals

]); let activeTab = ref(0);

</script>

<template>
  <Tabs :titles="titles" :active="activeTab" @setActive="activeTab = $event"></Tabs>
  <div class="container">
    <component :is="contents[activeTab]"></component>
  </div>
</template>

<style></style>