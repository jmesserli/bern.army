<template>
  <div class="container">
    <div class="row">
      <b-jumbotron
        header="bern.army"
        lead="Nützliches für Bewohner des Wpl BE"
        class="col-12"
      />
    </div>

    <b-row>
      <b-col sm="12" lg="6">
        <b-card title="Nächste Menüs">
          <b-card-text>
            <div v-if="nextMenus.length">
              <p>{{ nextMenuTitle }}</p>
              <div v-for="menu in nextMenus" :key="menu.name" class="pre-line">
                <h5 v-if="nextMenus.length > 1">
                  {{ menu.name }}
                </h5>
                <p>{{ menu.menu }}</p>
              </div>
            </div>

            <div v-else>
              Aktuell keine Informationen
            </div>
          </b-card-text>

          <n-link v-if="!nextMenus.length" to="/timeout" tag="b-button">
            Menuplan ansehen
          </n-link>
        </b-card>
      </b-col>

      <b-col sm="12" lg="6">
        <b-card title="Öffnungszeiten KP">
          <b-card-text>
            <table class="table table-sm table-borderless">
              <tbody>
                <tr>
                  <th scope="row">
                    Montag
                  </th>
                  <td class="text-right">
                    07:00 - 11:30 Uhr
                  </td>
                </tr>
                <tr>
                  <th scope="row" />
                  <td class="text-right">
                    12:30 - 18:30 Uhr
                  </td>
                </tr>

                    Dienstag
                  </th>
                  <td class="text-right">
                    07:00 - 11:30 Uhr
                  </td>
                </tr>
                <tr>
                  <th scope="row" />
                  <td class="text-right">
                    12:30 - 17:30 Uhr
                  </td>
                </tr>

                  <th scope="row">
                    Mittwoch
                  </th>
                  <td class="text-right">
                    07:00 - 11:30 Uhr
                  </td>
                </tr>
                <tr>
                  <th scope="row" />
                  <td class="text-right">
                    12:30 - 18:30 Uhr
                  </td>
                </tr>

                  <th scope="row">
                    Donnerstag
                  </th>
                  <td class="text-right">
                    07:00 - 11:30 Uhr
                  </td>
                </tr>
                <tr>
                  <th scope="row" />
                  <td class="text-right">
                    12:30 - 18:30 Uhr
                  </td>
                </tr>

                  <th scope="row">
                    Freitag
                  </th>
                  <td class="text-right">
                    07:00 - 11:30 Uhr
                  </td>
                </tr>
                <tr>
                  <th scope="row" />
                  <td class="text-right">
                    12:30 - 17:00 Uhr
                  </td>
                </tr>
              </tbody>
            </table>
          </b-card-text>
        </b-card>
      </b-col>
    </b-row>
  </div>
</template>

<script>
import moment from 'moment'
import menu from '~/assets/menu.json'

export default {
  components: {},
  computed: {
    isNextLunch() {
      const now = new Date()

      return (
        now.getHours() < 14 || (now.getHours() === 13 && now.getMinutes() < 15)
      )
    },
    isNextDinner() {
      const now = new Date()

      return (
        (now.getHours() > 13 ||
          (now.getHours() === 13 && now.getMinutes() >= 15)) &&
        now.getHours() < 19
      )
    },
    nextMenuTitle() {
      if (this.isNextLunch) {
        return 'Mittagessen (11:30 - 13:15 Uhr)'
      }
      if (this.isNextDinner) {
        return 'Nachtessen (17:30 - 19:00 Uhr)'
      }

      return ''
    },
    nextMenus() {
      if (menu.week < moment().isoWeek()) {
        return []
      }

      const dayOfWeek = moment().isoWeekday()
      // Schliesst Samstage und Sonntage aus
      // if (dayOfWeek < 1 || dayOfWeek > 5) {
      //   // Sat & Sun
      //   return []
      // }

      const dayMenus = menu.days.filter(function filter(x) {
        return typeof x !== 'string'
      })[dayOfWeek - 1]

      if (this.isNextLunch) {
        return [
          {
            name: 'Tagesteller',
            menu: dayMenus.tagesteller
          },
          {
            name: 'Pasta-Hit',
            menu: dayMenus['pasta-hit']
          }
        ]
      }
      if (this.isNextDinner) {
        return [
          {
            name: 'Nachtessen',
            menu: dayMenus.nachtessen
          }
        ]
      }

      return []
    }
  }
}
</script>

<style>
.pre-line {
  white-space: pre-line;
}
</style>
