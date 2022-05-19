<template>
  <div id="app">
    <!--<img alt="Vue logo" src="./assets/logo.png">-->
    <!--<HelloWorld msg="Welcome to Your Vue.js App"/>-->

    <div class="container">
      <div class="page-title">Welcome to Opportunity</div>
      <div class="page-date">{{ currentDateTime() }}</div>

      <ul v-if="entries" class="sections-container" >
        <li class="section" v-for="entry in entries" :key="entry.id">
          <span class="section-time">{{ entry[0] }}, {{ entry[1].replaceAll("/", ".") }}</span
          ><br />
          <h3 class="section-title">{{ entry [2]}}</h3>
          <span class="section-body">{{ entry [3]}}</span
          ><br />

          <span></span>
        </li>
      </ul>

    <div v-else class="notWorking"> 
      <p> This is not working, please try again later </p>

    </div>

    </div>
    <footer>
      <img
        class="home-logos"
        src="./assets/zurich-offices-image.png"
        alt="zuri-logo"
      />
      <img class="home-logos" src="./assets/opportunity.png" alt="zuri-logo" />
      <img class="home-logos" src="./assets/sag-logo.png" alt="zuri-logo" />
    </footer>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      title: "Welcome to Opportunity",
      sheet_id: "1a81aI0Y8ViZO0tI92h2YSMqVQJ8hmNNMyMylXgvwiU4",
      api_token: "AIzaSyA-qeDXOhEeQDA0vQf7LgkF7DQtGnAtmAU",
      // entries: [],
      dateTime: "",
    };
  },
  computed: {
    gsheet_url() {
      return `https://sheets.googleapis.com/v4/spreadsheets/${this.sheet_id}/values:batchGet?ranges=A2%3AE100&valueRenderOption=FORMATTED_VALUE&key=${this.api_token}`;
    },
  },
  methods: {
    // <!--date_function: function () {
    //   var currentDate = new Date();
    //   console.log(currentDate);
    //   var formatted_date = new Date().toJSON().slice(0, 10).replace(/-/g, "/");
    //   console.log(formatted_date);
    // },
    refreshData(){
      this.currentDateTime();
      this.getData();
      

    },


    currentDateTime() {
      const current = new Date();
      const day = current.getDate();
      const month = current.getMonth() + 1;
      const year = current.getFullYear();

      const dateTime = day + "." + month + "." + year;

      if (month < 10) {
        return day + "." + "0" + month + "." + year;
      }
      return dateTime;
    },

    getData() {
      axios.get(this.gsheet_url).then((response) => {
        this.entries = response.data.valueRanges[0].values;
      });
    },
  },
  mounted() {
    this.refreshData();
    setInterval(this.refreshData, 1000 * 60 * 30);
  },
};
</script>

<style>
@media screen and (max-width: 600px) {
  .section-title {
    font-size: 18px;
  }
  .page-title {
    font-size: 12px;
  }
  .page-date {
    font-size: 12px;
  }
}
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700;900&display=swap%");
html,
body,
ul {
  margin: 0px;
  padding: 0px;
}
body {
  /* margin: 0px;
  padding: 0px; */
  font-family: "Inter";
  /* background-position: center;
  background-size: cover; */
  /* display: flex; */
  /* flex-direction: column; */
  /* justify-content: space-between; */
  min-height: 100vh;
  background-color: #e5e5e5;
}
/* ul {
  margin: 0px;
  padding: 0px;
} */
#app {
  /* background-color: #e5e5e5; */
  /* color: rgb(255, 255, 255); */
  /* max-width: 100vw; */
  /* width: auto; */
  /* align-self: center; */
  display: flex;
  flex-direction: column;
  /* align-content: center; */
}

.container {
  margin: 60px;
}
header {
  justify-items: center;
  width: auto;
  height: 60px;
  text-align: left;
  /* font-family: "Inter"; */
  font-weight: 700;
  font-size: 22px;
  color: black;
  /* margin-left: 3rem; */
}
.page-title {
  font-size: 62px;
  color: #323d4a;
  font-family: "Inter";
  font-weight: 900;
}
.page-date {
  font-size: 62px;
  color: #9aa7b1;
  /* font-family: "inter"; */
  font-weight: 500;
}
.sections-container {
  display: block;
}
.section {
  font-size: 28px;
  font-style: normal;
  /*display: flex;*/
  list-style-type: none;
  max-width: auto;
  /* width: 60vw; */
  /* height: 150px; */
  margin-bottom: 1.5rem;
  /* margin-left: 1rem; */
  background: #0f05a0;
  padding: 30px;
}
.section-time {
  color: #eb5e00;
  /* font-family: "Inter"; */
  /* font-style: normal; */
  /* font-size: 28px; */
  font-weight: 900;
  /* padding-left: 2rem; */
}
.section-title {
  color: #ffbfab;
  /* font-family: "Inter"; */
  /* font-size: 28px; */
  font-weight: 800;
  /* padding-left: 2rem; */
}
.section-body {
  color: #ffbfab;
  /* font-family: "Inter"; */
  /* font-size: 28px; */
  font-weight: 450;
  /* padding-left: 2rem; */
}
footer {
  background-color: rgb(255, 255, 255);
  /* max-width: 100vw; */
  /* width: 100%; */
  flex-direction: row;
  /* align-content: center; */
  display: flex;
  margin-top: auto;
}
.home-logos {
  max-width: 100%;
  width: 13vw;
  margin: 1rem;
  margin-left: auto;
  margin-right: auto;
}
</style>
