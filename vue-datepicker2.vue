<template>
  <div
    :data-date="date"
    :data-format="format"
    class="input-append date"
  >
    <input
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
    date: String,

    // Options:
    format: String,
    inputClass: String,
    clearBtn: Boolean,
    // NOTE: capitalization differs from datepicker option.
    autoClose: Boolean,
    todayHighlight: Boolean,
  },

  mounted() {
    const options = {
      clearBtn: this.clearBtn,
      autoclose: this.autoClose,
      todayHighlight: this.todayHighlight,
    };

    const dp2 = $(this.$el).datepicker(options);
    dp2.on('changeDate', (ev) => {
      this.$emit('change', ev.date);
    });
  },
}
</script>

<style scoped>

</style>