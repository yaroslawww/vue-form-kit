<template>
  <div
    v-if="title"
    :class="['form-title', `form-title-h${level}`]"
  >
    {{ title }}
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
      type: Number,
      default: 2,
    },
  },
};
</script>
