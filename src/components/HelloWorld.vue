<template>
  <div>
    <!--
      * ref와 reactive의 차이점
      ref : String, Number, Object 등 어떠한 타입에서도 사용 가능
      reactive : Object, Array, Map, Set과 같은 타입에서만 사용 가능
    -->
    <div class="name">{{ name }}</div>
    <button type="button" @click="updateName">Click</button>
    <div class="name2">{{ name2 }}</div>
    <button type="button" @click="updateName2">+ Click</button>
    <button type="button" @click="updateName3">- Click</button>

    <div class="cnt">{{ cnt }}</div>
    <button type="button" @click="onClickAdd">+++</button>
    
    <br><br>
    <div>{{ age }}</div>
  </div>
</template>

<script>
import { ref, reactive, computed } from 'vue'

export default {
  name: 'HelloWorld',
  // props: {
  //   msg: String
  // },
  setup() {
    const name = ref('Summer');

    const updateName = () => {
      name.value = "Yeonsu"
    }

    const name2 = reactive({
      id: 1,
    })

    let cnt = ref(0);

    let age = ref(17);

    const updateName2 = () => {
      if(name2.id == 10){
        alert("최대 10");
        return;
      }
      name2.id = name2.id + 1;
    }

    const updateName3 = () => {
      if(name2.id == 0){
        return;
      }
      name2.id = name2.id - 1;
    }

    const onClickAdd = () => {
      cnt.value++
      console.log(cnt.value)
    }

    // const getAge = (computed) => {
    //   return age.value >= 18? "Yes" : "No";
    // }
    const getAge = computed(() => {
      return age.value >= 18? "Yes" : "No";
    })
    console.log(getAge, getAge.value);

    return{
      name,
      updateName,
      name2,
      updateName2,
      updateName3,
      cnt,
      onClickAdd,
      age,
      getAge
    }
  }
}
</script>