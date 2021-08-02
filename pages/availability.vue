<template>
  <div>
    <v-date-picker class="mt-12" color="primary"
      v-model="picker" multiple width="500"
      year-icon="mdi-calendar-blank"
      prev-icon="mdi-skip-previous"
      next-icon="mdi-skip-next"
    ></v-date-picker>

    <div class="d-flex">
      <v-icon color="primary" x-small>fiber_manual_record</v-icon> <span class="primary--text ml-5">Booked</span> <span class="ml-6" style="color: #707070; opacity: 0.4;">Orange shaded dates are booked days</span></div>
      <div class="d-flex mt-3">
      <v-icon color="#F4F3F0" x-small>fiber_manual_record</v-icon> <span style="color: #4D4D4D;" class=" ml-5">Available</span> <span class="ml-6" style="color: #707070; opacity: 0.4;">Unshaded dates are free days</span>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      picker: new Date(Date.now() - new Date().getTimezoneOffset() * 60000)
        .toISOString()
        .substr(0, 10),
    }
  },
}
</script>
