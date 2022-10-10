<template>
  <div>
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>
  </div>
</template>

<script>
import { computed, inject } from 'vue';

export default {
  props: ['firstName', 'lastName'],
  setup(props, context) {
    const userName = computed(function () {
      return props.firstName + ' ' + props.lastName;
    });

    const age = inject('userAge');

    // Context includes 3 objects:
    // attrs, is anything that is passed as an attribute to the component, but it is not a prop, requireds a root element.
    // slots, which give us access to whatever is passed as sloth to the component.
    // emits, which allows us to emit custom events
    // context.emit('save-data'. 1);  // it is equivalent to this.$emit('save-data, 1); is options API.

    console.log(context);

    return {
      userName,
      age,
    };
  },
};
</script>
