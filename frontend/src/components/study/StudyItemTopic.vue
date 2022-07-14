<template>
  <div>
    <h1>
      Topic is
      <span class="topic-color">
<!--        {{$route.query.topic}}-->
        {{topic}}
      </span>
    </h1>

    <div v-if="topic === 'Composition-Api'">
      <h5>Link :
        <a href="https://v3.ko.vuejs.org/guide/composition-api-introduction.html" target="_blank">
          Vue 공식 문서 - composition api (ko)
        </a>
      </h5>
      composition api 작성 예정
    </div>

    <div v-else>
      작성 예정
    </div>

  </div>
</template>

<script setup>

import { useRoute } from "vue-router/dist/vue-router";

const route = useRoute();
const topic = route.params.topic;

</script>

<style scoped>
  .topic-color {
    color: hsla(160, 100%, 37%, 1);
  }
</style>