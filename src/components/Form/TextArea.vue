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
    <textarea
      :id="id"
      :value="modelValue"
      :name="name"
      :autocomplete="autocomplete"
      :required="required"
      :disabled="disabled"
      class="form-input-text form-input-textarea w-full"
      :placeholder="placeholder"
      :maxlength="maxlength"
      :cols="cols"
      :rows="rows"
      @input="(event) => $emit('update:modelValue', event.target.value)"
    />
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
  name: 'FormTextArea',
  props: {
    modelValue: {
      type: String,
      default: '',
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
    cols: {
      type: [Number, String],
      default: null,
    },
    rows: {
      type: [Number, String],
      default: null,
    },
  },
  emits: ['update:modelValue'],
};
</script>
