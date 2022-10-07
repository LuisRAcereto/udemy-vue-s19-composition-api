<template>
  <section class="container">
    <h2>{{ username }}</h2>
    <h2>{{ age }}</h2>
    <button @click="setAge">Change Age</button>
  </section>
</template>

<script>
// import { reactive } from 'vue';
import { ref } from 'vue';

export default {
  setup() {
    const uName = ref('Maximilian');
    const uAge = ref(31);
    // const user = reactive({
    //   name: 'Maximilian',
    //   age: 31,
    // });

    function setNewAge() {
      // user.age = 32;
      uAge.value = 32;
    }

    return {
      // user: user,
      username: uName,
      age: uAge,
      setAge: setNewAge,
    };
  },
  // data() {
  //   return {
  //     userName: 'Maximilian',
  //     age: 31,
  //   };
  // },
  // methods:{
  //   setAge(){
  //     this.age = 33;
  //   }
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>
