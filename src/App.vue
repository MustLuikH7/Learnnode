<script setup>
import { ref } from 'vue';
import Modal from "./Components/Modal.vue"
let modalActive = ref(false)
</script>
<template>
  <div class="container">
    <button class="button is-primary" @click="modalActive = true">Open modal</button>
    <Modal :active="modalActive" @close="modalActive = false"></Modal>
  </div>
</template>
