<script setup>
  defineProps({
    choice: {
      type: String,
      required: true,
    }
  })

  const emit = defineEmits(['pickChoice'])

  const removeChoice = () => {
    emit('removeChoice')
  }
</script>

<template>
  <div class="choice-item">
    <span class="choice-text">{{ choice }}</span>
    <span @click="removeChoice" class="remove-button">×</span>
  </div>

</template>

<style scoped>
.choice-item {
    background: white;
    border: 1px solid #f0f0f0;
    border-radius: 14px;
    padding: 16px 18px;
    margin-bottom: 10px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.04);
}

.choice-text {
    font-size: 16px;
    color: #333;
    font-weight: 500;
}

.remove-button {
    color: #ff4757;
    font-size: 24px;
    font-weight: 600;
    cursor: pointer;
    line-height: 1;
}

</style>
