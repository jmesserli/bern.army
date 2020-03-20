<template>
  <div class="container">
    <h1 class="mt-3">
      Restaurant Time out
      <small v-if="menu" class="text-muted">
        Menüplan KW <span>{{ menu.week }}</span>
      </small>
    </h1>

    <div v-if="menu">
      <div v-if="outdated">
        <p>Der Menüplan der aktuellen Woche wurde noch nicht abgetippt.</p>
        <b-button
          v-b-toggle.menu-collapse
          size="sm"
          variant="secondary"
          class="mb-3"
        >
          Menüplan der letzten Woche
        </b-button>
      </div>
      <b-collapse id="menu-collapse" :visible="!outdated">
        <b-table-lite
          head-variant="dark"
          :small="true"
          :fields="fields"
          :items="menu.days"
          :responsive="true"
        />
      </b-collapse>
    </div>
    <div v-else="">
      <p>Es scheint als könnte das Menu nicht geladen werden.</p>
    </div>

    <h3>Essenszeiten</h3>
    <div class="container">
      <div class="row">
        <table class="table table-sm table-borderless col-md-6 col-sm-12">
          <tbody>
            <tr>
              <th scope="row">
                Frühstück
              </th>
              <td class="text-right">
                06:00 - 07:15 Uhr
              </td>
            </tr>
            <tr>
              <th scope="row">
                Mittagessen
              </th>
              <td class="text-right">
                11:30 - 13:00 Uhr
              </td>
            </tr>
            <tr>
              <th scope="row">
                Nachtessen
              </th>
              <td class="text-right">
                17:30 - 18:45 Uhr
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import moment from 'moment'
import menu from '~/assets/menu.json'

const dayOfWeek = moment().isoWeekday()

export default {
  data() {
    return {
      fields: [
        'tag',
        'tagesteller',
        { key: 'pasta-hit', label: 'Pasta-Hit' },
        'nachtessen'
      ],
      menu: {
        week: menu.week,
        days: menu.days
          .filter(function noString(x) {
            return typeof x !== 'string'
          })
          .map(
            (function mapper() {
              const weekdays = [
                'Montag',
                'Dienstag',
                'Mittwoch',
                'Donnerstag',
                'Freitag',
                'Samstag',
                'Sonntag'
              ]
              let num = 1
              return function map(x) {
                x.tag = weekdays[num - 1]
                x._rowVariant = dayOfWeek === num ? 'success' : 'default'

                num++
                return x
              }
            })()
          )
      }
    }
  },
  computed: {
    outdated() {
      const isoWeek = moment().isoWeek()
      return isoWeek !== this.menu.week
    }
  }
}
</script>

<style>
table.b-table td {
  white-space: pre-line;
}
</style>
