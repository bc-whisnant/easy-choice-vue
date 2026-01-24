<script setup>
defineProps({
  text: {
    type: String,
    required: true,
  },
  subtext: {
    type: String,
    required: true
  }
})
</script>

<template>
  <div class="greetings">
    <h1>{{ text }}</h1>
    <h3>
      {{ subtext }}
    </h3>
  </div>
</template>

<style scoped>
.greetings {
  text-align: center;
}

h1 {
  font-size: 32px;
  font-weight: 800;
  margin-bottom: 8px;
}

h3 {
  font-size: 15px;
  opacity: 0.9;
}


h1,
h3 {
  color: white;
}
</style>
