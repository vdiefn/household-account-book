<script setup lang="ts">
import { ref, onMounted } from "vue"

const data = ref<{message?:string}>({})

const getMessage = async() => {
  try {
    const res = await fetch("https://household-account-book-api.onrender.com/api/message",{
      method: "GET",
      headers: {
        "accept":"application/json"
      }
    })
    data.value = await res.json()
  }catch(err){
    console.error(err)
  }
}

onMounted(() => {
  getMessage()
})
</script>

<template>
  <p>{{ data.message }}</p>
</template>

<style scoped>
</style>
