<script setup>
import {ref } from 'vue'

const test = ref('Je suis un test')

</script>

<template>
    <p contenteditable="true">{{test}}</p>
</template>