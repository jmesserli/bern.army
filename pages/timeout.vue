<template>
  <div class="container">
    <h1 class="mt-3">
      Restaurant Time out
      <small class="text-muted">
        Menüplan KW <span>{{ menu.week }}</span>
      </small>
    </h1>

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
        week: 34,
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
              'Schweinsragout\nan Senfbiersauce, Gemüsemischung und Kartoffelstock',
            'pasta-hit':
              'Conchiglie al Carbonara\n(mit Speck, Zwiebeln und Petersilie an Rahmsauce)\noder Tomatensauce',
            nachtessen:
              'Gemüse-Lasagne\nmit Auberginen, Zucchetti, Peperoni und Mozzarella',
            _rowVariant: dayOfWeek === 1 ? 'success' : 'default'
          },
          {
            tag: 'Dienstag',
            tagesteller:
              'Dorschfilet\nmit Tomatenkruste an Morgenrotsauce, Blattspinat und Trockenreis\nDessert',
            'pasta-hit':
              'Conchiglie con Pesto\n(Basilikum, Pinienkerne, Sbrinz und Olivenöl)',
            nachtessen:
              'Schweinsbratwurst\nmit Kräutersenf und Kartoffel-Gemüsepfanne',
            _rowVariant: dayOfWeek === 2 ? 'success' : 'default'
          },
          {
            tag: 'Mittwoch',
            tagesteller:
              'Pouletgeschnetzeltes\nmit Ananas an Kokoscurrysauce, Cous Cous und Erbsen',
            'pasta-hit':
              'Conchiglie con Salmone\n(Rauchlachs, Zwiebeln, Lauch und Dill an Weissweinsauce)\noder Tomatensauce',
            nachtessen:
              "Spaghetti all'amatriciana\n(mit Zwiebeln, Knoblauch, Speck und Pfefferschoten an Tomatensauce)",
            _rowVariant: dayOfWeek === 3 ? 'success' : 'default'
          },
          {
            tag: 'Donnerstag',
            tagesteller:
              'Paniertes Schweinsschnitzel\nBlumenkohlgratin und Spinatnudeln\nDessert',
            'pasta-hit':
              'Conchiglie alla Bella Vita\n(Pouletbruststreifen mit Zwiebeln und Knoblauch an Tomatenrahmsauce)\noder Tomatensauce',
            nachtessen: 'Churer-Fleischtorte\nund Mischsalat',
            _rowVariant: dayOfWeek === 4 ? 'success' : 'default'
          },
          {
            tag: 'Freitag',
            tagesteller:
              'Wiener Kalbsrahmgoulasch\nKarottenscheiben und Polenta',
            'pasta-hit':
              'Conchiglie Cinque P\n(Tomatenrahmsauce mit Pfeffer, Petersilie und Sbrinz)',
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
