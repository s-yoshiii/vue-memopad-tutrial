<script setup>
import { computed } from "@vue/runtime-core";
import { useRoute } from "vue-router";
import { useStore } from "vuex";
import MemoForm from "@/components/MemoForm.vue";
const route = useRoute();
const store = useStore();
const memo = computed(() => {
  const id = parseInt(route.params.id);
  return store.getters.getMemoById(id);
});
</script>

<template>
  <h2>Edit id:{{ route.params.id }}</h2>
  <MemoForm />
  {{ memo.title }}
</template>

<style></style>
