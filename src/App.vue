<template>
  <section class="container">
    <h2>{{ user.name }}</h2>
    <h2>{{ user.age }}</h2>
  </section>
</template>

<script>
import { reactive } from 'vue';
// import { ref } from 'vue';

export default {
  setup() {
    // const uName = ref('Maximilian');
    // const uAge = ref(31);

    // Here is the example using ref for an object
    // const user = ref({
    //   name: 'Maximilian',
    //   age: 31,
    // });
    // Now using reactive that only receives as parameter objects:
    const user = reactive({
      name: 'Maximilian',
      age: 31,
    });

    console.log(user);

    setTimeout(function () {
      // uName.value = 'Max';
      // uAge.value = 32;
      // When using ref, properties of an object must be access via "value" property.
      // user.value.name = 'Max';
      // user.value.age = 32;
      // In contrast to when using ref, reactive allows to access directly to the fields of the object:
      user.value = 'Max';
      user.value = 32;
    }, 2000);

    return {
      user: user,
    };
  },
  // data() {
  //   return {
  //     userName: 'Maximilian',
  //   };
  // },
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
