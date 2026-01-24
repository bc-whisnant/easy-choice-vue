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
      margin-bottom: 24px;
  }

</style>  