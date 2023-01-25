<script setup>
import { computed } from "vue";
import { useStore } from "vuex";
const store = useStore();
const memos = computed(() => {
  return store.state.memos;
});
const hasMemos = computed(() => {
  return store.state.memos.length > 0;
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
