<template>

<!--    <RouterLink to="/study/detail" :topic="topic">-->
  <RouterLink :to="{path: `/study/${topic}`}">
    {{topic}}
  </RouterLink>

</template>

<script setup>
  defineProps({
    topic: {
      type: String,
      required: true,
    },
  });
</script>

<style scoped>
</style>