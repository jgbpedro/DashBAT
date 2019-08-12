<template lang="pug">
  div
    span {{msg}} 
    i.fa.fa-toggle-on.text-success(v-if="paramToCheck", @click="toggle")
    i.fa.fa-toggle-off(v-else, @click="toggle")
</template>

<script>
export default {
  props: {
    msg: String,
    paramToCheck: Boolean,
    toggle: Function
  }
};
</script>
