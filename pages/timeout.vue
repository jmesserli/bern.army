<template>
  <div class="container">
    <h1 class="mt-3">
      Restaurant Timeout <small class="text-muted">Menüplan</small>
    </h1>

    <table class="table table-sm mt-3 table-responsive-md">
      <thead class="thead-dark">
        <tr>
          <th scope="col">
            Tag
          </th>
          <th scope="col">
            Tagesteller
          </th>
          <th scope="col">
            Pasta-Hit
          </th>
          <th scope="col">
            Nachtessen
          </th>
        </tr>
      </thead>
      <tbody>
        <tr id="d-1">
          <th scope="row">
            Montag
          </th>
          <td>
            <p>Schweinsragout mit Tomaten</p>
            <p>Broccoli und Kartoffel-Gnocchi</p>
          </td>
          <td>
            <p>Conchiglie ai Funghi</p>
            <p>(Steinpilze und Zwiebeln an Tomatensauce)</p>
          </td>
          <td>
            <p>Wurst-Käsesalat</p>
            <p>Schalenkartoffeln</p>
          </td>
        </tr>

        <tr id="d-2">
          <th scope="row">
            Dienstag
          </th>
          <td>
            <p>
              <abbr title="Herkunft: Polen">Seelachs</abbr> in Knusperpanade
            </p>
            <p>mit Kräuterquarksauce,</p>
            <p>Blattspinat und Salzkartoffeln</p>
            <b>Dessert</b>
          </td>
          <td>
            <p>Conchiglie alla Nonna</p>
            <p>(Rahmsauce mit Speck-, Schinken-,</p>
            <p>Tomaten- und Peperoniwürfel)</p>
            <p>oder Tomatensauce</p>
          </td>
          <td>
            <p>Spätzli-Pfanne</p>
            <p>mit Gemüsewürfeln</p>
            <p>und Champignons</p>
            <p>an Sauerrahmsauce</p>
          </td>
        </tr>

        <tr id="d-3">
          <th scope="row">
            Mittwoch
          </th>
          <td>
            <p>Pouletoberschenkel</p>
            <p>auf Peperonicoulis,</p>
            <p>Zucchetti und Tomatennudeln</p>
          </td>
          <td>
            <p>Conchiglie Alfredo</p>
            <p>(Rahmsauce mit Zwiebeln,</p>
            <p>Petersilie und Sbrinz)</p>
          </td>
          <td>
            <p>Rinds Meat Balls</p>
            <p>an Tomatensauce,</p>
            <p>gebratener Reis mit</p>
            <p>Gemüse und Ei</p>
          </td>
        </tr>

        <tr id="d-4">
          <th scope="row">
            Donnerstag
          </th>
          <td>
            <p>Paniertes Schweinsschnitzel</p>
            <p>Erbsen und Karotten</p>
            <p>Kartoffelgratin</p>
            <b>Dessert</b>
          </td>
          <td>
            <p>Conchiglie con Mortadel</p>
            <p>(Mortadella, Zwiebeln und</p>
            <p>Peperoni an Pestorahmsauce)</p>
            <p>oder Tomatensauce</p>
          </td>
          <td>
            <p>Tortelloni mit Spinat</p>
            <p>und Ricottafüllung</p>
            <p>an Cinque <b>&pi;</b> Sauce</p>
          </td>
        </tr>

        <tr id="d-5">
          <th scope="row">
            Freitag
          </th>
          <td>
            <p>Ungarisches Gulasch</p>
            <p>mit Grünen Bohnen</p>
            <p>und Pilav-Reis</p>
          </td>
          <td>
            <p>Conchiglie al Tonno</p>
            <p>(Thunfisch, Sardellen und</p>
            <p>Oliven an Tomatensauce)</p>
            <p>oder Tomatensauce</p>
          </td>
          <td class="text-muted">
            <p>Nachtessen nur</p>
            <p>auf Vorbestellung</p>
            <p>Menü nach Ansage</p>
          </td>
        </tr>

        <tr>
          <td colspan="4">
            Salatbüffet mit verschiedenen frischen Salaten
          </td>
        </tr>
      </tbody>
    </table>

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

<style></style>
