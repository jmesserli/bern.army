<template>
  <div class="container">
    <h1 class="mt-3">
      Restaurant <i>Treffpunkt</i>
      <small class="text-muted">
        Menüplan KW <span>{{ menu.week }}</span>
      </small>
    </h1>

    <b-alert show dismissible variant="warning">
      Das Restaurant Time out ist vom Montag, 22. Juli bis am Freitag, 9. August
      geschlossen. Während dieser Zeit können sämtliche Mahlzeiten im
      <a href="https://goo.gl/maps/8mZWiJUm8wsVBGZbA" class="alert-link">
        Restaurant Treffpunkt</a
      >
      neben der Mehrzweckhalle eingenommen werden.
    </b-alert>

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
        :fields="menu.fields"
        :items="menu.items"
        :responsive="true"
      />
    </b-collapse>

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
                11:30 - 13:15 Uhr
              </td>
            </tr>
            <tr>
              <th scope="row">
                Nachtessen
              </th>
              <td class="text-right">
                17:30 - 19:00 Uhr
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>

    <!-- <h3>Original Menüplan</h2>

      <img src="menueplan.jpg" class="img-fluid" alt="Menüplan" /> -->
  </div>
</template>

<script>
import moment from 'moment'

const dayOfWeek = moment().day()

export default {
  data() {
    return {
      menu: {
        week: 32,
        fields: [
          'tag',
          'tagesteller',
          { key: 'pasta-hit', label: 'Pasta-Hit' },
          'nachtessen'
        ],
        items: [
          {
            tag: 'Montag',
            tagesteller:
              'Schweinshalsbraten\nmit Senfsauce, Karottenscheiben und Spiralen',
            'pasta-hit':
              'Cellentani al Carbonara\n(Speck, Zwiebeln und Petersilie an Rahmsauce)\noder Tomatensauce',
            nachtessen:
              'Gemüsefrühlingsrolle\nmit süss-saurer Sauce, Risi e Bisi',
            _rowVariant: dayOfWeek === 1 ? 'success' : 'default'
          },
          {
            tag: 'Dienstag',
            tagesteller:
              'Dorschfilet auf Tomatensauce\nBlattspinat und Würfelkartoffeln\nDessert',
            'pasta-hit':
              'Gefüllte Pasta con Pesto\n(Basilikum, Pinienkerne, Sbrinz und Olivenöl)',
            nachtessen:
              'Penne al Cosimo\n(mit Speck und Artischocken an Tomatensauce)\noder Tomatensauce',
            _rowVariant: dayOfWeek === 2 ? 'success' : 'default'
          },
          {
            tag: 'Mittwoch',
            tagesteller:
              'Kalbsbratwurst\nmit Zwiebelsauce, Ratatouille und Rösti',
            'pasta-hit':
              'Cellentani con Salmone\n(Weissweinsauce mit Rauchlachs, Zwiebeln, Lauch und Dill)\noder Tomatensauce',
            nachtessen: 'Kichererbsen-Stroganoff\nund Pilav Reis',
            _rowVariant: dayOfWeek === 3 ? 'success' : 'default'
          },
          {
            tag: 'Donnerstag',
            tagesteller:
              'Poulet Ragout "Havanna-Style"\nan Kokos-Korriandersauce, Kräutertomate und Spinatnudeln\nDessert',
            'pasta-hit':
              'Cellentani Bolognese\n(Rindshackfleisch und Gemüse)\noder Tomatensauce',
            nachtessen:
              'Cheeseburger\nmit Coleslaw-Salat und Kartoffelschnitzen',
            _rowVariant: dayOfWeek === 4 ? 'success' : 'default'
          },
          {
            tag: 'Freitag',
            tagesteller:
              'Kalbsrahmgeschnetzeltes\nmit Champignons, Zucchettischeiben und wilder Reis',
            'pasta-hit':
              'Gefüllte Pasta Cinque P\n(Tomatenrahmsauce mit Pfeffer, Petersilie und Sbrinz)',
            nachtessen: 'Abends geschlossen\nLunchbestellung bis zum Frühstück',
            _rowVariant: dayOfWeek === 5 ? 'success' : 'default'
          }
        ]
      }
    }
  },

  computed: {
    outdated() {
      const isoWeek = moment().week()
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
