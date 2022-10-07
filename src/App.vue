<template>
  <section class="container">
    <h2>{{ username }}</h2>
    <h2>{{ age }}</h2>
    <button @click="setAge">Change Age</button>
    <div>
      <input type="text" placeholder="First Name" @input="setFirstName" />
      <input type="text" placeholder="Last Name" @input="setLastName" />
    </div>
  </section>
</template>

<script>
// import { reactive } from 'vue';
import { ref, computed } from 'vue';

export default {
  setup() {
    // const uName = ref('Maximilian');
    const firstName = ref('');
    const lastName = ref('');
    const uAge = ref(31);
    // const user = reactive({
    //   name: 'Maximilian',
    //   age: 31,
    // });

    // this must be imported from vue library and implements a computed property.
    // just
    const uName = computed(function () {
      return firstName.value + ' ' + lastName.value;
    });

    function setNewAge() {
      // user.age = 32;
      uAge.value = 32;
    }

    function setFirstName(event) {
      firstName.value = event.target.value;
    }

    function setLastName(event) {
      lastName.value = event.target.value;
    }

    return {
      // user: user,
      username: uName,
      age: uAge,
      setAge: setNewAge,
      setFirstName,
      setLastName,
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
