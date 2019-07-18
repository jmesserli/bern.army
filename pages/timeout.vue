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
        week: 29,
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
              'Schweinsragout mit Tomaten\nBroccoli und Kartoffel-Gnocchi',
            'pasta-hit':
              'Conchiglie ai Funghi\n(Steinpilze und Zwiebeln an Tomatensauce)',
            nachtessen: 'Wurst-Käsesalat\nSchalenkartoffeln',
            _rowVariant: dayOfWeek === 1 ? 'success' : 'default'
          },
          {
            tag: 'Dienstag',
            tagesteller:
              'Seelachs in Knusperpanade\nmit Kräuterquarksauce, Blattspinat und Salzkartoffeln\nDessert',
            'pasta-hit':
              'Conchiglie alla Nonna\n(Rahmsauce mit Speck-, Schinken-, Tomaten- und Peperoniwürfel)\noder Tomatensauce',
            nachtessen:
              'Spätzli-Pfanne\nmit Gemüsewürfeln und Champignons an Sauerrahmsauce',
            _rowVariant: dayOfWeek === 2 ? 'success' : 'default'
          },
          {
            tag: 'Mittwoch',
            tagesteller:
              'Pouletoberschenkel\nauf Peperonicoulis, Zucchetti und Tomatennudeln',
            'pasta-hit':
              'Conchiglie Alfredo\n(Rahmsauce mit Zwiebeln, Petersilie und Sbrinz)',
            nachtessen:
              'Rinds Meat Balls\nan Tomatensauce, gebratener Reis mit Gemüse und Ei',
            _rowVariant: dayOfWeek === 3 ? 'success' : 'default'
          },
          {
            tag: 'Donnerstag',
            tagesteller:
              'Paniertes Schweinsschnitzel\nErbsen und Karotten, Kartoffelgratin\nDessert',
            'pasta-hit':
              'Conchiglie con Mortadella\n(Mortadella, Zwiebeln und Peperoni an Pestorahmsauce)\noder Tomatensauce',
            nachtessen:
              'Tortelloni mit Spinat und Ricottafüllung\nan Cinque Pi Sauce',
            _rowVariant: dayOfWeek === 4 ? 'success' : 'default'
          },
          {
            tag: 'Freitag',
            tagesteller:
              'Ungarisches Gulasch\nmit grünen Bohnen und Pilav-Reis',
            'pasta-hit':
              'Conchiglie al Tonno\n(Thunfisch, Sardellen und Oliven an Tomatensauce)\noder Tomatensauce',
            nachtessen: 'Nachtessen nur auf Vorbestellung\nMenü nach Ansage',
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
