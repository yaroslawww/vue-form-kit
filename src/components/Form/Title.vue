<template>
  <div
    :class="['form-title', `form-title-h${level}`, (required===false?'':'form-input-label--required')]"
  >
    <slot>
      {{ title }}
    </slot>
  </div>
</template>

<script>
export default {
  name: 'FormTitle',
  props: {
    title: {
      type: String,
      default: null,
    },
    level: {
      type: [Number, String],
      default: 2,
    }, required: {
      type: [String, Boolean],
      default: false,
    },
  },
};
</script>
