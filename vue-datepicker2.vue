<template>
  <div
    v-bind:data-format="format"
    class="input-append date"
  >
    <input
      :class="inputClass"
      type="text"
      ref="input"
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
      $(this.$el).datepicker('setDate', this.date);
    },
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
      })
      .on('clearDate', () => {
        this.$emit('change', null);
      });

    if (this.date) {
      $(this.$el).datepicker('setDate', this.date);
    }
  },
}
</script>

<style scoped>

</style>
