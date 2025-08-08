<script setup lang="ts">
import { ref, onMounted } from "vue";

const data = ref<{message?:string}>({});
const getMessage = async() => {
  try {
    const res = await fetch("https://household-account-book-api.onrender.com/api/message", {
      method: "GET",
      headers: {
        "Accept": "application/json",
      },
    });

    data.value = await res.json();
  }catch(err){
    console.error(err);
  }
};



onMounted(() => {
  getMessage();
});
</script>

<template>
  <h1>You did it!</h1>
  <p>
    {{ data.message }}
  </p>
  <ElButton type="success">開始</ElButton>
</template>

<style scoped></style>
