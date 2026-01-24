<script setup>
  import Choice from './Choice.vue';

  defineProps({
    choices: {
      type: Array,
      required: true,
    }
  })
</script>


<template>
  <div class="choices-list">
    <Choice v-for="(choice, index) in choices" :key="index" :choice="choice" />
  </div>
</template>

<style scoped>
  .choices-list {
    max-height: 40vh;
    margin-bottom: 24px;
    overflow-y: scroll;
  }

</style>  