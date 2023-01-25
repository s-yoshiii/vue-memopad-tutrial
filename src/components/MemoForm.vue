<script setup>
import { ref, toRef, defineProps } from "vue";
import { useRouter } from "vue-router";
import { useStore } from "vuex";
const props = defineProps(["memo"]);
const memo = toRef(props, "memo");
const store = useStore();
const router = useRouter();
const tl = ref(memo.value.title);
const cont = ref(memo.value.content);
const save = (tl, cont) => {
  let tempMemo = {
    title: tl,
    content: cont,
    id: null,
  };
  if (memo.value.id) {
    tempMemo.id = memo.value.id;
  }
  if (!tl) {
    alert("タイトルは必須です");
    return;
  }
  store.commit("save", tempMemo);
  router.push("/");
};
const remove = () => {
  store.commit("delete", memo.value.id);
  router.push("/");
};
</script>

<template>
  <div><input type="text" v-model="tl" /></div>
  <div><textarea cols="30" rows="10" v-model="cont"></textarea></div>
  <div class="center">
    <button type="button" @click="save(tl, cont)">保存</button>
    <button type="button" v-if="props.memo.id" @click="remove()">削除</button>
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
