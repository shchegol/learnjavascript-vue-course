<template>
    <input ref="datepicker" :value="value" :placeholder="placeholder" type="text">
</template>

<script>
  import flatpickr from 'flatpickr'
  import { ru } from 'flatpickr/dist/l10n/ru';
  import 'flatpickr/dist/flatpickr.css';

  export default {
    name: 'Datepicker',
    props: {
      value: {
        type: String,
        default: ''
      },
      placeholder: {
        type: String,
        default: 'Set date'
      }
    },
    data: () => ({
      flatpickr: null
    }),
    watch: {
      value: 'updateDatepicker'
    },
    methods: {
      initDatepicker() {
        this.flatpickr = flatpickr(this.$refs.datepicker, {
          locale: "ru",
          dateFormat: 'd.m.Y',
          onChange: (selectedDates, dateStr) => {
            this.$emit('input', dateStr);
          }
        });
      },
      updateDatepicker() {
        if (this.flatpickr) {
          this.flatpickr.setDate(this.value);
        }
      },
    },
    mounted() {
      this.initDatepicker();
    }
  }
</script>
