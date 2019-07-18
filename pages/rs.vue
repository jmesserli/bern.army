<template>
  <div class="container">
    <h1 class="mt-3">
      RS-Woche
    </h1>
    <div v-for="rs in rsItems" :key="rs.name">
      <RsWoche
        v-if="showRs(rs)"
        :name="rs.name"
        :rs-start="rs.start"
        :rs-end="rs.rsEnd"
        :dd-end="rs.ddEnd"
      />
    </div>
  </div>
</template>

<script>
import moment from 'moment'
import RsWoche from '~/components/rs-woche.vue'

export default {
  components: { RsWoche },
  data() {
    return {
      rsItems: [
        {
          name: 'Start 19-1',
          start: moment('20190114'),
          rsEnd: moment('20190621'),
          ddEnd: moment('20191106')
        },
        {
          name: 'Start 19-2',
          start: moment('20190624'),
          rsEnd: moment('20191025'),
          ddEnd: moment('20200415')
        },
        {
          name: 'Start 20-1',
          start: moment('20200113'),
          rsEnd: moment('20200515'),
          ddEnd: moment('20201104')
        },
        {
          name: 'Start 20-2',
          start: moment('20200622'),
          rsEnd: moment('20201023'),
          ddEnd: moment('20210414')
        }
      ]
    }
  },
  methods: {
    showRs(rs) {
      return rs.start.isBefore(moment()) && rs.ddEnd.isAfter(moment())
    }
  }
}
</script>
