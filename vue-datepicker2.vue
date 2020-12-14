<template>
  <div
    v-bind:data-date="date"
    v-bind:data-format="format"
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
    date: Date,

    // Options:
    format: String,
    inputClass: String,
    clearBtn: Boolean,
    // NOTE: capitalization differs from datepicker option.
    autoClose: Boolean,
    todayHighlight: Boolean,
  },

  watch: {
    date(newDate) {
      console.log(`Watch:date: ${newDate}`);
      $(this.$el).datepicker('setValue', newDate);
    }
  },

  mounted() {
    const options = {
      clearBtn: this.clearBtn,
      autoclose: this.autoClose,
      todayHighlight: this.todayHighlight,
    };

    $(this.$el).datepicker(options)
      .on('changeDate', (ev) => {
        this.$emit('change', ev.date);
      });

    $(this.$el).datepicker('setValue', this.date);
  },
}
</script>

<style scoped>

</style>