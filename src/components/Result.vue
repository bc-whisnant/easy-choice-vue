<script setup>
  defineProps({
    result: {
      type: String,
      required: true
    }
  })

</script>


<template>
  <div class="result-section">
    <p class="result-label">Your choice is:</p>
    <div class="result-box">{{ result }}</div>
  </div>
</template>

<style scoped>
  .result-section {
    text-align: center;
  
  }
  .result-label {
    color: #666;
    font-size: 14px;
    margin-bottom: 12px;
  }

  .result-box {
    background: linear-gradient(135deg, #ffc837 0%, #ff8008 100%);
    color: white;
    padding: 20px 24px;
    border-radius: 18px;
    font-size: 24px;
    font-weight: 800;
    box-shadow: 0 6px 20px rgba(255, 136, 8, 0.4);
  }
</style>