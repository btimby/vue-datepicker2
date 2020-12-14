<template>
  <div class="input-append date">
    <input
      v-bind:value="value"
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

    const dp2 = $(this.$el).datepicker(options);
    dp2.on('changeDate', (ev) => {
      console.log(`dp2.changeDate`, ev);
      this.value = ev.date;
    });
  },
}
</script>

<style scoped>

</style>