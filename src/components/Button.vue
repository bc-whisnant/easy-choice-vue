<script setup>
  defineProps({
    buttonIcon: {
      type: String,
      required: false
    },
    buttonText: {
      type: String,
      required: true
    },
    disabled: {
      type: Boolean,
      required: false
    }
  })
  const emit = defineEmits(['pickChoice'])

  const pickChoice = () => {
    emit('pickChoice')
  } 

</script>


<template>  
  <button @click="pickChoice" :disabled="disabled" class="choice-button" :class="disabled && 'disabled'">
    <span>{{ buttonIcon }}</span>
    {{ buttonText }}
  </button>
</template>


<style scoped>
  .choice-button {
    width: 100%;
    background: linear-gradient(135deg, #5b68e6 0%, #7c5dde 100%);
    border: none;
    border-radius: 18px;
    padding: 18px;
    color: white;
    font-size: 18px;
    font-weight: 700;
    cursor: pointer;
    box-shadow: 0 6px 20px rgba(91, 104, 230, 0.4);
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    margin-bottom: 24px;
  }

</style>  
