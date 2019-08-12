<template lang="pug">
  div
    span {{msg}} 
    i.fa.fa-toggle-on.text-success(v-if="paramToCheck")
    i.fa.fa-toggle-off(v-else)
</template>

<script>
export default {
  props: {
    msg: String,
    paramToCheck: Boolean
  }
};
</script>
