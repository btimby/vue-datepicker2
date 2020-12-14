<template>
    <input
      v-model="value"
      type="text"
    >
    <slot></slot>
</template>

<script>
export default {
  name: 'VueDatepicker2',

  props: {
    value: null,

    options: {
      clearBtn: true,
      autoclose: true,
      todayHighlight: true,
    }
  },

  mounted() {
    $(this.$el).datepicker(this.options);
  },
}
</script>

<style scoped>

</style>