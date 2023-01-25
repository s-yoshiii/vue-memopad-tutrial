<script setup>
import { computed } from "vue";
import { useStore } from "vuex";
const store = useStore();
const memos = computed(() => {
  return store.getters.getAll;
});
const hasMemos = computed(() => {
  return store.getters.getCount;
});
</script>
<template>
  <div class="home">
    <ul v-if="hasMemos">
      <li v-for="memo in memos" :key="memo.id">{{ memo.title }}</li>
    </ul>
    <p v-else>メモがありません。</p>
  </div>
</template>
