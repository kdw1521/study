<template>
  <div>
    <h1>
      Topic is
      <span class="topic-color">
        {{topic}}
      </span>
    </h1>

    <div v-if="topic === 'Composition-Api'">
<!--     <composition-api />-->
      <CompositionApi exampleProp="wando"/>
    </div>

    <div v-else>
      작성 예정
    </div>

  </div>
</template>

<script setup>

import { useRoute } from "vue-router/dist/vue-router";
import CompositionApi from "./composition/CompositionApi.vue"
import { provide, reactive, readonly, ref } from "vue";

const route = useRoute();
const topic = route.params.topic;

// provide
const company = ref('Smart Score')
const user = reactive({
  name: 'wando',
  age: 30
})
provide('company', readonly(company))
provide('user', readonly(user))

const updateCompany = arg => {
 company.value = arg
}
provide('updateCompany', updateCompany)

</script>

<style scoped>
  .topic-color {
    color: hsla(160, 100%, 37%, 1);
  }
</style>