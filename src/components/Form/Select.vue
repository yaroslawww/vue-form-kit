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
    <SelectStandard
      :id="id"
      :model-value="modelValue"
      :options="options"
      :name="name"
      :label="label"
      :required="required"
      class="w-full"
      @update:model-value="$emit('update:modelValue', $event)"
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
  name: 'FormSelect',
  props: {
    modelValue: {
      type: String,
      default: '',
    },
    options: {
      type: Array,
      default: () => [],
    },
    label: {
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
    required: {
      type: [String, Boolean],
      default: false,
    },
  },
  emits: ['update:modelValue'],
};
</script>
