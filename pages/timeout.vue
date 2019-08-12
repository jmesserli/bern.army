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
        week: 33,
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
              'Schweins-Gyros\nan Sauerrahmsauce mit grünen Bohnen und neuen Kartoffeln',
            'pasta-hit':
              'Penne ai Funghi\n(mit Steinpilzen und Zwiebeln an Tomatensauce)',
            nachtessen:
              'Bärner Hörnli-Auflauf\nmit Cervelat, Vorderschinken und Rüebli',
            _rowVariant: dayOfWeek === 1 ? 'success' : 'default'
          },
          {
            tag: 'Dienstag',
            tagesteller:
              'Paniertes Seelachsfilet\nmit Tartaresauce, Broccoliröschen und Trockenreis\nDessert',
            'pasta-hit':
              'Penne alla Nonna\n(mit Speck, Schinken, Tomaten und Peperoni an Rahmsauce)\noder Tomatensauce',
            nachtessen: 'Gemüse-Rösti\nmit Raclettekäse überbacken',
            _rowVariant: dayOfWeek === 2 ? 'success' : 'default'
          },
          {
            tag: 'Mittwoch',
            tagesteller:
              'Rindfleischvogel\nmit zweifarbigen Rüebli und Kräuterkartoffelstock',
            'pasta-hit':
              'Penne Alfredo\n(Rahmsauce mit Zwiebeln, Sbrinz und Petersilie)',
            nachtessen: "Tortelloni\nall'arrabiata",
            _rowVariant: dayOfWeek === 3 ? 'success' : 'default'
          },
          {
            tag: 'Donnerstag',
            tagesteller:
              'Poulet Cordon-Bleu\nPeperonatagemüse und Weissweinrisotto',
            'pasta-hit':
              'Penne con Mortadella\n(mit Mortadella, Zwiebeln und Pereroni an Pestorahmsauce)\noder Tomatensauce',
            nachtessen:
              'St. Galler-Schüblig\nKartoffelsalatmit Eiern und Essiggurken',
            _rowVariant: dayOfWeek === 4 ? 'success' : 'default'
          },
          {
            tag: 'Freitag',
            tagesteller:
              'Hackbraten\nmit Rotweinsauce, Blumenkohl und Tomatennudeln\nDessert',
            'pasta-hit':
              'Penne al Tonno\n(mit Thunfisch, Sardellen und Oliven an Tomatensauce)',
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
