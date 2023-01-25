<script setup>
import { ref } from "@vue/reactivity";
import { useRouter } from "vue-router";
import { useStore } from "vuex";
const store = useStore();
const router = useRouter();
const tl = ref("");
const cont = ref("");
const save = (tl, cont) => {
  let memo = {
    title: tl,
    content: cont,
  };
  store.commit("save", memo);
  router.push("/");
};
</script>

<template>
  <div><input type="text" v-model="tl" /></div>
  <div><textarea cols="30" rows="10" v-model="cont"></textarea></div>
  <div class="center">
    <button type="button" @click="save(tl, cont)">保存</button>
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
