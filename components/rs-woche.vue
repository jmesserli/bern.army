<template>
  <b-card :title="name" class="mb-2">
    <p>
      RS-Woche: {{ week }} / {{ displayTotal }}
      <span v-if="week > 18">(Durchdiener)</span>
    </p>

    <b-progress :max="displayTotal">
      <b-progress-bar
        :value="rsWeek"
        :variant="week <= 18 ? 'primary' : 'success'"
        :animated="week <= 18"
      />
      <b-progress-bar
        :value="ddWeek"
        :variant="week > 18 && week <= totalWeeks ? 'primary' : 'success'"
        :animated="week > 18 && week <= totalWeeks"
      />
    </b-progress>
  </b-card>
</template>

<script>
import moment from 'moment'

export default {
  name: 'RsWoche',
  props: ['name', 'rsStart', 'rsEnd', 'ddEnd'],
  computed: {
    week() {
      return Math.ceil(moment().diff(this.rsStart, 'weeks', true))
    },
    rsWeek() {
      return Math.min(18, this.week)
    },
    ddWeek() {
      return Math.max(0, this.week - 18)
    },
    totalWeeks() {
      return Math.ceil(this.ddEnd.diff(this.rsStart, 'weeks', true))
    },
    displayTotal() {
      return this.week <= 18 ? 18 : this.totalWeeks
    }
  }
}
</script>
