<template>
  <div>
    <input
      v-model="value"
      :class="inputClass"
      type="text"
    >
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'VueDatepicker2',

  props: {
    value: null,
    inputClass: null,

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