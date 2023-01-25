<script setup>
import { useRoute } from "vue-router";
const route = useRoute();
</script>

<template>
  <div>Edit View{{ route.params.id }}</div>
</template>

<style></style>
