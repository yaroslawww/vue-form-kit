<template>
  <div
    class="form-input-wrap"
    :class="{'has-validation-error': !!error}"
  >
    <label
      v-if="label"
      :for="id"
      class="form-input-label"
    >
      {{ label }}
    </label>
    <span
      v-if="modelValue"
      class="form-input-action"
      @click.prevent="hidePassword = !hidePassword"
    >
      <slot
        v-if="hidePassword"
        name="show-button"
      >
        Show
      </slot>
      <slot
        v-else
        name="hide-button"
      >
        Hide
      </slot>
    </span>
    <input
      :id="id"
      :value="modelValue"
      :name="name"
      :type="hidePassword?'password':'text'"
      :autocomplete="autocomplete"
      :required="required"
      class="form-input-text w-full"
      :placeholder="placeholder"
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
import { ref } from 'vue';

export default {
  name: 'FormPassword',
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
    required: {
      type: [String, Boolean],
      default: false,
    },
  },
  emits: ['update:modelValue'],
  setup() {
    const hidePassword = ref(true);

    return {
      hidePassword,
    };
  },
};
</script>
