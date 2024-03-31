<template>

  <head>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css">
    <link rel="icon" type="image/png" href="logo.png">
  </head>

  <body>
    <header>
      <nav class="navbar navbar-light" style="background-color: rgba(36, 235, 142, 0.5);">

        <a class="navbar-brand" href="index.html">
          <img src="logo.png" width="30" height="30" class="d-inline-block align-top">
          ClimateAction Alliance
        </a>

        <div>
          <button type="button"  @click="setLanguage(false)">Deutsch</button>
          <button type="button" @click="setLanguage(true)">Hebräisch</button>
        </div>

        <div class="navbar-expand">
          <ul class="navbar-nav">
            <li class="nav-item">
              <a class="nav-link" href="link.html">Jobs</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="link.html">Hilfe</a>
            </li>
          </ul>
        </div>

      </nav>
    </header>

    <main>
      <br>
      <div id="format" class="flex-container" :class="{ heb: getLanguage() }">
        <nav>
          <ul class="nav flex-column">
            <li class="nav-item">
              <a class="nav-link" href="#section1">Wer wir sind</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#section2">CO<sub>2</sub> Emissionsdaten</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#section3">Spenden</a>
            </li>
          </ul>
        </nav>

        <div id="mainSection" style="width: 100%;">
          <section>
            <h2 id="section1">Wer wir sind</h2>
            <p> Wir setzen uns ein im Kampf gegen den Klimawandel! <br>
              Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore
              et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum.
              Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit
              amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna
              aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd
              gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur
              sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam
              voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea
              takimata sanctus est Lorem ipsum dolor sit amet. Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat, vel illum dolore
              eu feugiat nulla facilisis at vero eros et accumsan et iusto odio dignissim qui blandit praesent luptatum
              zzril delenit augue duis dolore te feugait nulla facilisi. Lorem ipsum dolor sit amet.</p>

            <h2 id="section2">Tabelle mit CO<sub>2</sub> Emissionsdaten</h2>
            <ag-grid-vue id="table" domLayout="autoHeight" :rowData="rowData" :columnDefs="colDefs"
              :gridOptions="gridOptions" class="ag-theme-quartz" style="width: 100%;">
            </ag-grid-vue>

            <br>
            <h2 id="section3">Spenden</h2>
            <p>Wir freuen uns über Ihre Unterstützung in Form einer Spende. <br>
              Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore
              et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum.
              Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit
              amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna
              aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd
              gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur
              sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam
              voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea
              takimata sanctus est Lorem ipsum dolor sit amet. Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat, vel illum dolore
              eu feugiat nulla facilisis at vero eros et accumsan et iusto odio dignissim qui blandit praesent luptatum
              zzril delenit augue duis dolore te feugait nulla facilisi. Lorem ipsum dolor sit amet.</p>
          </section>

        </div>
      </div>
    </main>

    <footer style="background-color: #b9b9b9;">
      <div class="container d-flex justify-content-center">
        <ul>
          <li class="d-inline"><a href="link.html">Datenschutz</a></li>
          <li class="d-inline" style="margin-left: 10px;"><a href="link.html">Impressum</a></li>
        </ul>
      </div>
    </footer>

  </body>

</template>

<script>
import { ref } from 'vue';
import "ag-grid-community/styles/ag-grid.css"; 
import "ag-grid-community/styles/ag-theme-quartz.css"; 
import { AgGridVue } from "ag-grid-vue3"; 

export default {
  name: "App",

  components: {
    AgGridVue, 
  },

  data() {

    return {
      language: false,
    }
    
  },

  methods: {

    setLanguage(lng) {
      this.language = lng;
    },

    getLanguage() {
      return this.language;
    },

  },

  setup() {

    const colDefs = ref([
      { field: "Land", filter: true, floatingFilter: true, suppressHeaderMenuButton: true, wrapText: true, autoHeight: true, flex: 1 },
      { field: "Firma", filter: true, floatingFilter: true, suppressHeaderMenuButton: true, wrapText: true, autoHeight: true, flex: 1 },
      { field: "CO₂-Emission/ Jahr (t)", filter: false, autoHeight: true,  flex: 1},
    ]);

    const gridOptions = {  
      defaultColDef: {
        wrapHeaderText: true,
        autoHeaderHeight: true,
      },
    };

    const rowData = ref([
      { Land: "Ungarn", Firma: "Evergreen Technologies", "CO₂-Emission/ Jahr (t)": 2373 },
      { Land: "Frankreich", Firma: "Summit Solutions", "CO₂-Emission/ Jahr (t)": 5836 },
      { Land: "Deutschland", Firma: "Horizon Innovations", "CO₂-Emission/ Jahr (t)": 586 },
      { Land: "Frankreich", Firma: "Solaris Enterprises", "CO₂-Emission/ Jahr (t)": 7534 },
      { Land: "Italien", Firma: "EcoVision Inc.", "CO₂-Emission/ Jahr (t)": 4836 },
      { Land: "Bulgarien", Firma: "BlueSky Industries", "CO₂-Emission/ Jahr (t)": 890 },
      { Land: "Spanien", Firma: "TerraTech Solutions", "CO₂-Emission/ Jahr (t)": 8936 },
      { Land: "England", Firma: "GreenLeaf Group", "CO₂-Emission/ Jahr (t)": 1038 },
      { Land: "Spanien", Firma: "Renewal Dynamics", "CO₂-Emission/ Jahr (t)": 3275 },
    ]);

    return {
      rowData,
      colDefs,
      gridOptions,
    };

  },

};
</script>

<style>

@media screen and (min-width: 768px) {

  .flex-container {
    display: flex;
  }

  #mainSection {
    width: 50% !important;
  }

  .heb {
    flex-direction: row-reverse;
    text-align: right;
  }

}


.heb {
  text-align: right;
}

#format {
  margin-left: 5px;
  margin-right: 5px;
}

#table {
  text-align: center;
}

.ag-header-cell-label {
  justify-content: center;
}

.ag-cell-wrap-text {
  word-break: break-word;
}
</style>
