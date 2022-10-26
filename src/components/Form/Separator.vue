<template>
  <div
    :class="['form-separator', `form-separator-h${level}`, symmetric !== false?'form-separator--symmetric':'']"
  />
</template>

<script>
export default {
  name: 'FormSeparator',
  props: {
    level: {
      type: Number,
      default: 1,
    },
    symmetric: {
      type: [Boolean, String],
      default: false,
    },
  },
};
</script>
