<template>
  <component
    :is="`${$formKitConfigs.componentPrefix}FormInputWrapper`"
    :id="id"
    :label="label"
    :error="error"
    :required="required"
    :input-wrap-class="inputWrapClass"
  >
    <template
      v-for="(_, name) in $slots"
      #[name]="slotData"
    >
      <slot
        :name="name"
        v-bind="slotData"
      />
    </template>
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
      :disabled="disabled"
      class="form-input-text w-full"
      :placeholder="placeholder"
      @input="(event) => $emit('update:modelValue', event.target.value)"
    >
  </component>
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
    disabled: {
      type: [String, Boolean],
      default: false,
    },
    inputWrapClass: {
      type: [String, Object, Array],
      default: null,
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
