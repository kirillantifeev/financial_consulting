<template>
  <div class="container__input">
    <div class="input__title"><slot></slot></div>
    <textarea
      v-if="multiline"
      class="input textarea"
      :placeholder="placeholder"
      :value="modelValue"
      @input="handleInput"
      @blur="handleBlur"
      rows="4"
    ></textarea>
    <input
      v-else
      class="input text"
      type="text"
      :placeholder="placeholder"
      :value="modelValue"
      @input="handleInput"
      @blur="handleBlur"
      :style="{
        height: heightProps,
        borderRadius: radiusProps,
        padding: paddingProps
      }"
    />
    <div v-if="errorMessage" class="error">{{ errorMessage }}</div>
  </div>
</template>

<script setup>
const props = defineProps({
  placeholder: String,
  modelValue: String,
  errorMessage: String,
  multiline: {
    type: Boolean,
    default: false
  }
});

const emit = defineEmits(['update:modelValue', 'blur']);

const handleInput = (e) => {
  emit('update:modelValue', e.target.value);
};

const handleBlur = () => {
  emit('blur');
};
</script>

<style scoped>
.container__input {
  width: 100%;
}

.input__title {
  font-family: 'Lato', sans-serif;
  font-weight: 400;
  font-size: 16px;
  color: var(--main-text);
  margin-bottom: 8px;
}

.input {
  box-sizing: border-box;
  width: 100%;
  border: 1px solid #C1C1C1;
  font-family: 'Lato', sans-serif;
  font-weight: 400;
  font-size: 16px;
  color: var(--main-text);

    &:focus {
    border-color: none;
    outline: none;
    box-shadow: 2px 3px 4px 2px rgba(0, 0, 0, 0.2);
  }
}


.textarea {
  resize: vertical; 
  min-height: 157px; 
  overflow-y: auto; 
  border-radius: 22px;
  padding: 22px 33px;
}

.text {
    border-radius: 52px;
    padding: 22px 33px;
}

.error {
  font-family: 'Lato', sans-serif;
  font-weight: 400;
  font-size: 12px;
  color: red;
  margin-top: 5px;
}
</style>