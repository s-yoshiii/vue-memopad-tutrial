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
      <li v-for="memo in memos" :key="memo.id">
        <a href="">{{ memo.title }}</a>
      </li>
    </ul>
    <p v-else>メモがありません。</p>
  </div>
</template>
<style scoped>
ul {
  margin: 0;
  padding: 0;
}
li {
  position: relative;
  list-style: none;
  border-bottom: 1px solid #ccc;
  padding-bottom: 10px;
  padding-left: 2em;
  margin-bottom: 10px;
}
li::before {
  position: absolute;
  top: 0.25em;
  left: 0.5em;
  content: "";
  display: inline-block;
  width: 1em;
  height: 0.5em;
  border-left: 2px solid #42b983;
  border-bottom: 2px solid #42b983;
  transform: rotate(-45deg);
}
li a {
  color: #42b983;
  text-decoration: none;
  display: block;
}
</style>
