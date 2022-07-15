<template>
  <div>

    <h5>Link :
      <a href="https://v3.ko.vuejs.org/guide/composition-api-introduction.html" target="_blank">
        Vue 공식 문서 - composition api (kr)
      </a>
    </h5>

    <ul class="mt-2">

      <li @click="changeShow('first')">1. Composition Api 의 필요성</li>
      <ul v-if="firstShow === true">
        <li class="li-square">
          options api 의 경우 prop, data, computed 등의 옵션의 규칙을 지켜 작성한다. <br>
          이렇게 작성하여 코드를 이해하기 위해 스크롤을 위, 아래로 이동하여 코드를 보는데 <br>
          <i>(* 이 행동을 <span class="color-brown">점프</span> 라고 표현함)</i> <br>
          점점 많은 주제가 추가될수록 코드의 양이 많아서 가독성 + 유지보수성이 매우 낮아진다. <br>
          이를 보완하기 위해 Composition Api가 등장했다. <br>
          <i>(* 동일한 논리적 관심사와 관련있는 코드를 배치하여 문제를 해결하려고 함)</i>
        </li>
      </ul>

      <li class="mt-1" @click="changeShow('second')">2. Composition Api 맛보기</li>
      <ul v-if="secondShow === true">
        <li class="li-square">
          <i>시작하기</i> <br>
          실제로 Composition Api 작업을 시작하려면, <br>
          실제로 사용할수 있는 부분이 있어야한다. <br>
          Vue 컴포넌트에서는 이 위치를 <span class="brown">setup</span> 이라고 부른다. <br>
        </li>

        <li class="li-square">
          <i>setup 컴포넌트 옵션</i> <br>
          setup 컴포넌트 옵션은 컴포넌트가 생성되기 전에, props가 한번 resolved될때 실행된다. <br>
          <i>(* setup이 실행될때 컴포넌트 인스턴스가 아직 생성되지않아 setup 옵션 내에 this가 존재하지않음. <br> 즉, props를 제외하고 다른 속성에 접근할수 없음.)</i>
        </li>

        <li class="li-square">
          <i>ref 반응성 변수</i> <br>
          화면 + 코드 보자.
        </li>

        <li class="li-square">
          <i>watch 를 사용해 변화에 반응</i> <br>
          화면 + 코드 보자.
        </li>

        <li class="li-square">
          <i>이렇게 맛을 보았으니 좀더 깊숙히 들어가보면 되겠다.</i>
        </li>
      </ul>

      <li class="mt-1" @click="changeShow('third')">3. Setup</li>
      <ul v-if="thirdShow === true">
        <li class="li-square">
          <i>setup 은 2가지 전달인자를 가지고 있다.</i>
          <ul>
            <li class="li-decimal" v-for="kind of setupKinds" :key="kind">
             {{kind}}
            </li>
          </ul>
        </li>

        <li class="li-square">
          <i>props</i> <br>
          setup 내부의 props는 반응성이 있고, 새로운 props가 전달되면 업데이트 된다. (현재 script setup에선 defineProps으로 사용)<br>
          <i class="color-orange">
            (* 주의: es6의 구조분해할당을 사용하면 props의 반응성이 제거 됨. <br>
            *개인적 생각: 한글판이 아닌 공식문서를 보면 script setup 안에 쓰면 구조분해 할당을 쓸일이 없어 신경쓰지 않아도 될것같음. <br>
            setup function(setup())을 이용하는 경우에 주의가 필요할것 같음.
            )</i>
        </li>

        <li class="li-square">
          <i>context</i> <br>
          context는 3가지 컴포넌트 프로퍼티를 가지는 일반 js 객체임. <br>
          (setup function 에서는 2번째 인자인데 script setup으로 사용할때 useContext가 없음. 좀더 찾아봐야 할것같음.)
        </li>
      </ul>

      <li class="mt-1" @click="changeShow('fourth')">4. Life Cycle</li>
      <ul v-if="fourthShow === true">
        life cycle hook에 'on'을 추가하여 접근 가능함. <br>
        예시는 코드로 보는게 나을거 같음.
      </ul>

      <li class="mt-1" @click="changeShow('fifth')">5. Provide / Inject</li>
      <ul v-if="fifthShow === true">
        <li class="li-square">
          Provide
        </li>
        2개의 파라미터를 통해 속성 정의
        <ul>
          <li class="li-decimal" v-for="kind of provideKinds" :key="kind">
            {{kind}}
          </li>
        </ul>
        코드로 확인! (StudyItemTopic.vue)

        <li class="li-square">
          Inject
        </li>
        2개의 파라미터를 통해 값을 받을 수 있음 <br>
        코드로 확인! (CompositionApi.vue)
        <ul>
          <li class="li-decimal" v-for="kind of injectKinds" :key="kind">
            {{kind}}
          </li>
        </ul>
        <div class="color-orange">
          Test: <br>
          provide 된 값 inject로 받은 값 <br>
          1 : {{company}} <br>
          2 : {{user}} <br>
          3 : (provide로 값을 안보냈을때) {{test}} <br>
        </div>

        <li class="li-square">
          반응성
        </li>
        provide된 값과 inject된 값 사이에 반응성을 추가하기 위해, 값을 provide할때 ref 나 reactive를 사용 할수 있음. <br>
        이렇게 하면 속성이 변경되면 inject 한 컴포넌트는 자동으로 업데이트가 된다. <br>
        코드로 확인! (StudyItemTopic.vue)

        <li class="li-square">
          반응성 속성 변경하기
        </li>
        반응성 있는 provide / inject값을 사용할때, 가능하면 provider 내부에서 변경이 발생하도록 유지는 것이 좋음. (공식문서에서 추천) <br>
        provider 에서 함수로 제공하는 방법을 사용 <br>
        <div class="color-orange">
          Test: <br>
          <div @click="updateCompany('change wando!')">Click me!!!!!</div>
        </div>
        <br>
        그래서 inject 쪽에서 데이터 변경되지 않도록 하려면 provide 속성에 readonly를 사용하는 것을 추천함 <br>

        코드로 확인! (StudyItemTopic.vue)
      </ul>

      <li class="mt-1" @click="changeShow('sixth')">6. Template Refs</li>
        <ul v-if="sixthShow === true">
          Composition Api를 사용할 때, reactive refs API 와 template refs의 개념이 통합된다. <br>
          템플릿 내 요소 또는 컴포넌트 인스턴스에 대한 참조를 얻기 위해, 평소대로 ref를 선언하고 setup function 혹은 script setup에서 반환할수 있다.
        </ul>
    </ul>

  </div>
</template>

<script setup>
import {
  inject,
  onBeforeMount,
  onBeforeUnmount,
  onBeforeUpdate,
  onErrorCaptured,
  onMounted,
  onRenderTracked,
  onRenderTriggered,
  onUnmounted,
  onUpdated,
  ref, watch
} from "vue";

const firstShow = ref(false);
const secondShow = ref(false);
const thirdShow = ref(false);
const fourthShow = ref(false);
const fifthShow = ref(false);
const sixthShow = ref(false);

const setupKinds = ['props', 'context']
const provideKinds = ['속성명(string)', '속성값']
const injectKinds = ['inject할 속성명', '기본값 (optional)']

// props
defineProps({
  exampleProp: {
    type: String,
  }
})

// emit
// const emit = defineEmits(['change', 'delete'])

// inject
const company = inject('company')
const user = inject('user')
const test = inject('test', 'wando가 설정한 기본값')
const updateCompany = inject('updateCompany')


const changeShow = (step) => {
  if (step === 'first') firstShow.value = !firstShow.value
  else if (step === 'second') secondShow.value = !secondShow.value
  else if (step === 'third') thirdShow.value = !thirdShow.value
  else if (step === 'fourth') fourthShow.value = !fourthShow.value
  else if (step === 'fifth') fifthShow.value = !fifthShow.value
  else if (step === 'sixth') sixthShow.value = !sixthShow.value
}

// watch
watch(firstShow, (newValue, oldValue) =>{
  console.log(`기존 값 : ${oldValue} / 변경 값 : ${newValue}`)
})
watch(secondShow, () => {console.log('second !!')})

onBeforeMount(() => {
  console.log(`onBeforeMount ! - mount 되기 전`)
})
onMounted(() => {
  console.log(`onMounted ! - mount 된 후`)
})
onBeforeUpdate(() => {
  console.log(`onBeforeUpdate ! - data 변경 후 랜더 되기 전`)
})
onUpdated(() => {
  console.log(`onUpdated ! - data 변경 후 랜더 된 후`)
})
onBeforeUnmount(() => {
  console.log(`onBeforeUnmount ! - unmount 되기 전`)
})
onUnmounted(() => {
  console.log(`onUnmounted ! - unmount 된 후`)
})
onErrorCaptured(() => {
  console.log(`onErrorCaptured !`)
})
onRenderTracked(() => {
  console.log(`onRenderTracked !`)
})
onRenderTriggered(() => {
  console.log(`onRenderTriggered !`)
})


</script>

<style scoped>
  .color-brown {
    color: brown;
  }
  .color-orange {
    color: orange;
  }
  .mt-1 {
    margin-top: 1em;
  }
  .mt-2 {
    margin-top: 2em;
  }
  .li-square {
    list-style-type: square;
  }
  .li-decimal {
    list-style-type: decimal;
  }

</style>