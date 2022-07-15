<template>
  <div class="study" >
    <h1>목차</h1>
    <ul>
      <li v-for="topic of topics" :key="topic">
        <StudyItem :topic="topic" />
      </li>
    </ul>
  </div>
</template>

<script setup>
import StudyItem from "../components/study/StudyItem.vue";

const topics = [
    "Start-Project",
    "Composition-Api",
]

</script>

<style scoped>
@media (min-width: 1024px) {
  .study {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>