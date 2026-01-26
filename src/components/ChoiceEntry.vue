<script setup>
import { ref } from 'vue'

defineProps({
  placeholder: {
    type: String,
    required: true,
  },
  disabled: {
    type: Boolean,
    required: false
  }
})

const emit = defineEmits(['addChoice'])
const currentChoice = defineModel()


const addChoice = () => {
  emit('addChoice')
} 

</script>

<template>
  <div class="choice-input">
   <div class="input-group">
      <div class="input-field">
        <input v-model="currentChoice" type="text" :placeholder="placeholder" />
      </div>
      <button @click="addChoice" :disabled="disabled" class="add-button" :class="disabled && 'disabled'">+</button>
    </div>
  </div>
</template>

<style scoped>
.choice-input {
    background: white;
    border-radius: 20px;
    padding: 16px;
    margin-bottom: 24px;
    box-shadow: 0 4px 12px rgba(91, 104, 230, 0.1);
}

.input-group {
    display: flex;
    gap: 12px;
}

.input-field {
  width: 82%;
}

.input-field input {
  flex: 1;
  border: 2px solid #e0e0ff;
  border-radius: 14px;
  padding: 14px 16px;
  font-size: 16px;
  color: #999;
  outline: none;
  width: 100%;
}

.add-button {
  width: 18%;
  height: 52px;
  background: linear-gradient(135deg, #5b68e6 0%, #7c5dde 100%);
  border: none;
  border-radius: 14px;
  color: white;
  font-size: 28px;
  font-weight: bold;
  cursor: pointer;
  box-shadow: 0 4px 12px rgba(91, 104, 230, 0.3);
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
