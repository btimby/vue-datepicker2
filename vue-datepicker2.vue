<template>
  <div class="input-append date">
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

    // Options:
    inputClass: null,
    clearBtn: false,
    // NOTE: capitalization differs from datepicker option.
    autoClose: false,
    todayHighlight: false,
  },

  mounted() {
    const options = {
      clearBtn: this.clearBtn,
      autoclose: this.autoClose,
      todayHighlight: this.todayHighlight,
    };

    $(this.$el).datepicker(options);
  },
}
</script>

<style scoped>

</style>