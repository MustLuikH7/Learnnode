<script setup>
import { ref } from 'vue';
let items = ref(['Sai', 'Piim', 'Viin', 'Õlu'])
let newItem = ref('')
function add(){
  if(newItem.value !== ''){
  items.value.push(newItem.value.trim())
  }
  newItem.value =''
}
</script>
<template>
  <div class="container"> 
    <div class="field has-addons mt-5">
      <div class="control is-expanded">
    <input class="input" type="text" v-model="newItem" @keypress.enter="add">
  </div>
  <div class="control">
        <button class="button is-info" @click="add">
          Add Item
        </button>
      </div>
      <div class="content">
        <h1>All Items</h1>
        <ul>
            <li v-for="item in items">{{ item }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>
