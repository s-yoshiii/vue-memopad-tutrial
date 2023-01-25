<script setup>
import { useStore } from "vuex";
const store = useStore();
const save = () => {
  let memo = {
    title: "メモのタイトルです。",
    content: "メモの内容です。",
  };
  store.commit("save", memo);
};
</script>

<template>
  <div><input type="text" /></div>
  <div><textarea cols="30" rows="10"></textarea></div>
  <div class="center">
    <button type="button" @click="save()">保存</button>
  </div>
</template>

<style scoped>
div {
  margin-bottom: 10px;
}
input[type="text"] {
  width: 100%;
}
textarea {
  width: 100%;
  height: 30em;
}
button {
  width: 5em;
  margin: 3px;
}
.center {
  text-align: center;
}
</style>
