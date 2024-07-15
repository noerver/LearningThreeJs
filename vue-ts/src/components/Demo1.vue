<template>
    <div>Hello Demo 01</div>
    <div id="content">{{ message }}</div>
</template>
<script setup lang="ts">
import { ref } from 'vue'

defineProps<{ msg: string }>()

const message = ref("test")


</script>