<script setup>
import {ref, defineCustomElement } from 'vue'
import customComp from './components/customComp.ce.vue';

function AddElement() {
  const ExampleElement = defineCustomElement(customComp)
  customElements.define('my-example', ExampleElement)
  const userSelection = window.getSelection();
  const range = userSelection.getRangeAt(0);
  const newNode = new ExampleElement();
  range.insertNode(newNode);
}
const HTML = ref('');

function getInnerHTML() {
   HTML.value = document.querySelector('.wrapper').getInnerHTML({includeShadowRoots: true})
}

</script>

<template>
  <div class="wrapper">
    <div class="test"></div>
    <div>
      <button @click="AddElement">click</button>
      <button @click="getInnerHTML">HTML</button>
    </div>
    <textarea  v-model="HTML"></textarea>

  </div>

</template>

<style>
.test {
  background-color: rgb(223, 195, 195);
  width: 300px;
  height: 100px;
}
textarea {
  width: 300px;
  height: 400px;
}
.wrapper{
  display: flex;
  flex-direction: column;
}
</style>