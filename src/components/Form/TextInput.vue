<template>
  <div
    class="form-input-wrap"
    :class="{'has-validation-error': !!error}"
  >
    <label
      v-if="label"
      :for="id"
      class="form-input-label"
      :class="[required===false?'':'form-input-label--required']"
    >
      {{ label }}
    </label>
    <input
      :id="id"
      :value="modelValue"
      :name="name"
      :type="type"
      :autocomplete="autocomplete"
      :required="required"
      :disabled="disabled"
      class="form-input-text w-full"
      :class="inputClass"
      :placeholder="placeholder"
      :maxlength="maxlength"
      @input="(event) => $emit('update:modelValue', event.target.value)"
    >
    <div
      v-if="error"
      class="form-validation-error"
    >
      {{ error }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'FormTextInput',
  props: {
    modelValue: {
      type: String,
      default: '',
    },
    inputClass: {
      type: [String, Array, Object],
      default: null,
    },
    label: {
      type: String,
      default: null,
    },
    placeholder: {
      type: String,
      default: null,
    },
    error: {
      type: String,
      default: null,
    },
    id: {
      type: String,
      default: null,
    },
    name: {
      type: String,
      default: null,
    },
    autocomplete: {
      type: String,
      default: null,
    },
    type: {
      type: String,
      default: null,
    },
    maxlength: {
      type: String,
      default: null,
    },
    required: {
      type: [String, Boolean],
      default: false,
    },
    disabled: {
      type: [String, Boolean],
      default: false,
    },
  },
  emits: ['update:modelValue'],
};
</script>
