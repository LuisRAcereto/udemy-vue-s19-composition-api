<template>
  <section class="container">
    <user-data :firstName="firstName" :lastName="lastName"></user-data>
    <button @click="setAge">Change Age</button>
    <div>
      <input type="text" placeholder="First Name" v-model="firstName" />
      <input type="text" placeholder="Last Name" ref="lastNameInput" />
      <button @click="setLastName">Set Last Name</button>
    </div>
  </section>
</template>

<script>
// import { reactive } from 'vue';
import { ref, computed, watch, provide } from 'vue';
import UserData from './components/UserData.vue';

export default {
  components: {
    UserData,
  },
  setup() {
    // const uName = ref('Maximilian');
    const firstName = ref('');
    const lastName = ref('');
    const lastNameInput = ref(null);
    const uAge = ref(31);
    // const user = reactive({
    //   name: 'Maximilian',
    //   age: 31,
    // });

    provide('userAge', uAge);

    // this must be imported from vue library and implements a computed property.
    // just
    const uName = computed(function () {
      return firstName.value + ' ' + lastName.value;
    });

    // Watching a single property or calcualted property
    // watch(uAge, function (newValue, oldValue) {
    //   console.log('Old age: ' + oldValue);
    //   console.log('New Age: ' + newValue);
    // });

    // watching more than one property or calculated property
    watch([uAge, uName], function (newValues, oldValues) {
      console.log('Old age: ' + oldValues[0]);
      console.log('New age: ' + newValues[0]);
      console.log('Old name: ' + oldValues[1]);
      console.log('New name: ' + newValues[1]);
    });

    function setNewAge() {
      // user.age = 32;
      uAge.value = 32;
    }

    function setLastName() {
      lastName.value = lastNameInput.value.value;
    }

    return {
      // user: user,
      username: uName,
      age: uAge,
      setAge: setNewAge,
      setLastName,
      firstName,
      lastName,
      lastNameInput,
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
  //   },
  // provide() {
  //     return { age: this.age };
  // }
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
