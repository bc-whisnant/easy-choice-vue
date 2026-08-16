<script setup>
  defineProps({
    label: {
      type: String,
      required: true
    },
    disabled: {
      type: Boolean,
      required: true
    },
    numberOfAttempts: {
      type: Number,
      required: true
    }
  })

  const emit = defineEmits(['decreaseNumberOfAttempts', 'increaseNumberOfAttempts'])

  const decreaseNumberOfAttempts = () => {
    emit('decreaseNumberOfAttempts')
  }

  const increaseNumberOfAttempts = () => {
    emit('increaseNumberOfAttempts')
  }


</script>

<template>
  <div class="attempts-section">
    <span class="attempts-label">{{ label }}</span>
    <div class="attempts-stepper">
      <button class="stepper-btn" :class="disabled && 'disabled'" :disabled="disabled" @click="decreaseNumberOfAttempts">−</button>
      <span class="attempts-value">{{  numberOfAttempts }}</span>
      <button class="stepper-btn" :class="disabled && 'disabled'" :disabled="disabled" @click="increaseNumberOfAttempts">+</button>
    </div>
  </div>

</template>

<style scoped>
.attempts-section {
  background: white;
  border-radius: 18px;
  padding: 14px 18px;
  margin-bottom: 16px;
  box-shadow: 0 4px 12px rgba(91, 104, 230, 0.1);
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.attempts-label {
  font-size: 14px;
  color: #555;
  font-weight: 600;
}

.attempts-stepper {
  display: flex;
  align-items: center;
  gap: 14px;
}

.stepper-btn {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  border: none;
  background: linear-gradient(135deg, #5b68e6 0%, #7c5dde 100%);
  color: white;
  font-size: 18px;
  font-weight: 700;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  box-shadow: 0 3px 8px rgba(91, 104, 230, 0.3);
}

.disabled {
  background-color: lightgray;
}

.attempts-value {
  font-size: 17px;
  font-weight: 800;
  color: #5b68e6;
  min-width: 16px;
  text-align: center;
}

.attempts-progress {
  font-size: 12px;
  color: #888;
  font-weight: 600;
  text-align: center;
  margin-bottom: 8px;
}
</style>
