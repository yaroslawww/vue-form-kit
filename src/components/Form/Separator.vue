<template>
  <div
    :class="['form-separator', `form-separator-h${level}`]"
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
  },
};
</script>
