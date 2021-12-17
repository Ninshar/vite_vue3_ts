<script setup lang="ts">
import { ref } from "vue";
import { useMainStore } from "@/store/mian";
import loginApi from "@/service/api/login/login";
defineProps<{ msg: string }>();
const mainStore = useMainStore();

const count1 = ref(3);

const count = ref(0);

const LoginPost = async () => {
  const data = await loginApi.login({ userName: "lin", passWord: "12345" });
  console.log(data);
};
const updateName = () => {
  // $patch 修改 store 中的数据
  mainStore.$patch({
    name: "名称被修改了,nameLength也随之改变了",
  });
};

console.log(import.meta.env.VITE_APP_WEB_URL);
</script>

<template>
  <h1 @click="LoginPost">
    {{ msg }}<br />
    用户名:{{ mainStore.name }}<br />长度:{{ mainStore.nameLength }}
  </h1>
  <button @click="updateName">修改store中的name</button>

  <p>
    Recommended IDE setup:
    <a href="https://code.visualstudio.com/" target="_blank">VSCode</a>
    +
    <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>
  </p>

  <p>See <code>README.md</code> for more information.</p>

  <p>
    <a href="https://vitejs.dev/guide/features.html" target="_blank">
      Vite Docs
    </a>
    |
    <a href="https://v3.vuejs.org/" target="_blank">Vue 3 Docs</a>
  </p>

  <button type="button" @click="count++">count is: {{ count }}</button>
  <p>
    Edit
    <code>components/HelloWorld.vue</code> to test hot module replacement.
  </p>
</template>

<style lang="scss" scoped>
a {
  color: $test-color;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}
</style>
