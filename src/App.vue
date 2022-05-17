<template>
  <div id="app">
    <!--<img alt="Vue logo" src="./assets/logo.png">-->
    <!--<HelloWorld msg="Welcome to Your Vue.js App"/>-->

    <div class="container">
      <div class="page-title">Welcome to Opportunity</div>
      <div class="page-date">08.08.2021</div>

      <ul class="sections-container">
        <li class="section">
          <div class="section-time">14.00 Uhr</div>

          <div class="section-title">Basisbeschäftigung Besuch</div>

          <div class="section-body">
            Interessierte für den zweiten Kurs werden uns besuchen
          </div>
        </li>

        <li class="section">
          <div class="section-time">14.00 Uhr</div>
          <div class="section-title">Basisbeschäftigung Besuch</div>
          <div class="section-body">
            Interessierte für den zweiten Kurs werden uns besuchen
          </div>
        </li>

        <li class="section">
          <div class="section-time">14.00 Uhr</div>
          <div class="section-title">Basisbeschäftigung Besuch</div>

          <div class="section-body">
            Interessierte für den zweiten Kurs werden uns besuchen
          </div>
        </li>

        


      </ul>
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

export default {
  name: "App",
  date() {
    return {
      title: "Welcome to Opportunity",
    };
  },
  components: {},
  methods: {
    date_function: function () {
      var currentDate = new Date();
      console.log(currentDate);
      var formatted_date = new Date().toJSON().slice(0, 10).replace(/-/g, "/");
      console.log(formatted_date);
    },
  },
  mounted() {
    this.date_function();
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
/*main {
  align-self: center;
  display: flex;
  background: #e5e5e5;
  width: 60%;
  flex-direction: column;
      
}*/
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
