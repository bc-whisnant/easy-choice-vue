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
    },
    resetState: {
      type: Boolean,
      required: true
    }
  })
  const emit = defineEmits(['pickChoice', 'choiceReset'])

  const pickChoice = () => {
    emit('pickChoice')
  } 

  const choiceReset = () => {
    emit('choiceReset')
  }

</script>


<template>  
  <button @click="resetState ? choiceReset() : pickChoice()" :disabled="disabled" class="choice-button" :class="disabled && 'disabled'" :resetState="resetState">
    <span>{{ buttonIcon }}</span>
    {{ buttonText }}
  </button>
</template>


<style scoped>
  .choice-button {
    -webkit-appearance: none;
    appearance: none;
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

  .disabled {
    background-color: lightgray;
  }

  .choice-button span {
    font-weight: normal;
    font-family: -apple-system, "Apple Color Emoji", sans-serif;
  }

</style>  
