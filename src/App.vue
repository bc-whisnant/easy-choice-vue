<script setup>
  import Heading from './components/Heading.vue';
</script>

<template>
  <header>

    <div class="wrapper">
      <Heading text="Easy Choice" subtext="Can't decide? Let us choose!" />
    </div>
  </header>

  <main>
  </main>
</template>

<style scoped>

  main {
    flex: 1;
    background: linear-gradient(180deg, #f3f0ff 0%, #ffffff 100%);
    padding: 24px;
    overflow-y: auto;
  }

@media (max-width: 500px) {
  header .wrapper {
    display: flex;
    flex-direction: column;
    padding: 20% 0 10% 0;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  }
}
</style>
