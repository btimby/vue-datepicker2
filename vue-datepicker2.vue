<template>
  <div class="input-append date ac-start-date-text">
    <input v-bind="value" type="text">
    <slot></slot>
  </div>
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