<template>
  <div class="container">
    <header class="main-header">
      <img class="header-logo" :src="headerLogo" alt="joystick-2" />
      <h1 id="my-header">{{ headerText }}</h1>
      <div class="header-objects">
        <div class="searchbar-and-btn">
          <form action="#">
            <div class="vld-parent">
              <loading
                :active="isLoading"
                :can-cancel="true"
                :on-cancel="onCancel"
                :is-full-page="fullPage"
              ></loading>

              <input
                class="searchbar"
                id="searchInput"
                type="text"
                placeholder="Search.."
                v-model="search"
                data-search
              />
              <button
                @click.prevent="doAjax"
                @click="functionSearch"
                class="btn-search"
                id="btnSearch"
                type="button"
              >
                <i class="fa fa-search"></i>
              </button>
            </div>
          </form>
        </div>
        <nav class="header">
          <div class="links">
            <a class="nav-links" :href="playstation.link" target="_blank">{{
              playstation.name
            }}</a>
            <a class="nav-links" :href="xbox.link" target="_blank">{{
              xbox.name
            }}</a>
            <a class="nav-links" :href="nintendo.link" target="_blank">{{
              nintendo.name
            }}</a>
          </div>
        </nav>
      </div>
    </header>
    <header class="sub-header">
      <h2 id="my-subheader">Lorem ipsum dolor sit amet consectetur</h2>

      <!-- INICIO CAROUSEL container -->

      <div id="myCarousel" class="carousel slide" data-ride="carousel">
        <!-- Indicators -->
        <ol class="carousel-indicators">
          <li
            type="button"
            data-target="#myCarousel"
            data-slide-to="0"
            class="active"
          ></li>
          <li type="button" data-target="#myCarousel" data-slide-to="1"></li>
          <li type="button" data-target="#myCarousel" data-slide-to="2"></li>
          <li type="button" data-target="#myCarousel" data-slide-to="3"></li>
          <li type="button" data-target="#myCarousel" data-slide-to="4"></li>
        </ol>

        <!-- Wrapper for slides -->
        <div class="carousel-inner" role="listbox">
          <div class="item active">
            <img
              class="sld-img"
              :src="tlouIIOnPage"
              alt="The Last of Us Part II"
            />
            <div class="carousel-caption"></div>
          </div>

          <div class="item">
            <img class="sld-img" :src="gowOnPage" alt="God of War" />
            <div class="carousel-caption"></div>
          </div>

          <div class="item">
            <img
              class="sld-img"
              :src="re2OnPage"
              alt="Resident Evil 2 Remake"
            />
            <div class="carousel-caption"></div>
          </div>

          <div class="item">
            <img
              class="sld-img uncharted"
              :src="unchartedOnPage"
              alt="Uncharted 4 - A Thief's End"
            />
            <div class="carousel-caption"></div>
          </div>

          <div class="item">
            <img
              class="sld-img"
              :src="crashOnPage"
              alt="Crash Bandicoot N' Sane Trilogy"
            />
            <div class="carousel-caption"></div>
          </div>
        </div>

        <!-- Left and right controls -->
        <a
          class="left carousel-control"
          href="#myCarousel"
          role="button"
          data-slide="prev"
        >
          <span
            class="glyphicon glyphicon-chevron-left"
            aria-hidden="true"
          ></span>
          <span class="sr-only">Previous</span>
        </a>
        <a
          class="right carousel-control"
          href="#myCarousel"
          role="button"
          data-slide="next"
        >
          <span
            class="glyphicon glyphicon-chevron-right"
            aria-hidden="true"
          ></span>
          <span class="sr-only">Next</span>
        </a>
      </div>

      <!--FIM DO CAROUSEL-->
      <div class="header-list">
        <h3 id="headerList" class="thirdHeader">
          Lorem ipsum dolor sit amet 3
        </h3>
      </div>
    </header>
    <aside>
      <div class="related-container">
        <h4>{{ asideHeader }}</h4>
        <ul id="relatedList" class="related-list">
          <li v-for="game in myTopFive" :key="game.Rank" class="related-post">
            <div class="bs-example">
              <a
                class="top-link"
                :href="`#gameModal${game.Rank}`"
                data-toggle="modal"
                @click="modalVideo"
              >
                <img
                  :alt="game.Name"
                  :src="require(`@/assets/${game.GamePhoto}`)"
                  width="100"
                  height="100"
                />
              </a>
              <div :id="`gameModal${game.Rank}`" class="modal fade">
                <div class="modal-dialog">
                  <div class="modal-content">
                    <div class="modal-header">
                      <button
                        @click="closeModalVideo"
                        type="button"
                        class="close"
                        :rank_id="`${game.Rank}`"
                        data-dismiss="modal"
                        aria-hidden="true"
                      >
                        X
                      </button>
                      <h4 class="modal-title">{{ game.Name }}</h4>
                    </div>
                    <div class="modal-body">
                      <iframe
                        :id="`${game.Rank}`"
                        width="560"
                        height="315"
                        :src="`${game.Game_URL}`"
                        title="YouTube video player"
                        frameborder="0"
                        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                        allowfullscreen
                      >
                      </iframe>
                    </div>
                  </div>
                </div>
              </div>
              <div>
                <p class="related-game">
                  {{ game.Name }}<br />
                  {{ relatedDescription.genre }}: {{ game.Genre }}<br />
                  {{ relatedDescription.year }}: {{ game.Year }}<br />
                  {{ relatedDescription.platform }}: {{ game.Platform
                  }}<br /><br />
                </p>
              </div>
            </div>
          </li>
        </ul>
      </div>
    </aside>
    <article class="all-items-game">
      <div>
        <ul>
          <li v-for="game in myJson" :key="game.Rank" class="itemGame">
            <item-game-component id="list" :item="game"> </item-game-component>
          </li>
          <div class="wrapper" />
        </ul>
      </div>
    </article>
  </div>
  <footer class="footer-distributed">
    <div class="footer-right">
      <a :href="footerData.twitter" target="_blank"
        ><i class="fa fa-twitter"></i
      ></a>
      <a :href="footerData.linkedin" target="_blank"
        ><i class="fa fa-linkedin"></i
      ></a>
      <a :href="footerData.github" target="_blank"
        ><i class="fa fa-github"></i
      ></a>
    </div>

    <div class="footer-left">
      <p class="footer-links">Projeto: Business Case</p>

      <p>{{ footerData.copy }}</p>
    </div>
  </footer>
</template>

<script>
import headerlogo from "/src/images/joystick-2.png";
import tlouII from "/src/images/banner-images/tlou.jpg";
import gow from "/src/images/banner-images/gow.jpg";
import re2 from "/src/images/banner-images/re2.png";
import uncharted from "/src/images/banner-images/uncharted.jpg";
import crash from "/src/images/banner-images/crash.jpg";
import ItemGameComponent from "./components/ItemGameComponent.vue";
import myJson from "./list/games.json";
// Import component
import Loading from "vue-loading-overlay";
// Import stylesheet
import "vue-loading-overlay/dist/vue-loading.css";

export default {
  components: {
    ItemGameComponent,
    Loading,
  },
  data: function () {
    return {
      headerText: "Business Case Vue",
      headerLogo: headerlogo,
      tlouIIOnPage: tlouII,
      gowOnPage: gow,
      re2OnPage: re2,
      unchartedOnPage: uncharted,
      crashOnPage: crash,
      myJson: myJson,
      isLoading: false,
      search: "",
      myTopFive: [],
      relatedDescription: {
        genre: "Gênero",
        year: "Ano de Lançamento",
        platform: "Plataforma",
      },
      playstation: {
        link: "https://www.playstation.com/pt-br/",
        name: "Playstation",
      },

      xbox: {
        link: "https://www.xbox.com/pt-BR",
        name: "Xbox",
      },

      nintendo: {
        link: "https://www.nintendo.com/pt_BR/?L000-11:ch=pdpd",
        name: "Nintendo",
      },

      asideHeader: "Top Games",

      footerData: {
        copy: "Copyright © 2022 by Davi Almeida. All rights reserved.",
        twitter: "https://twitter.com/DaviVianaz",
        linkedin: "https://www.linkedin.com/in/almeidavi/",
        github: "https://github.com/daviialmeidaa",
      },
    };
  },
  methods: {
    functionSearch() {
      let text = this.search.toLowerCase(); // pegando a string e transformando em caixa baixa
      const stringFiltrada = myJson.filter((game) => {
        //filtrando o array myJson por uma string
        return (
          game.Name.toString().toLowerCase().includes(text) ||
          game.Platform.toString().toLowerCase().includes(text) ||
          game.Year.toString().toLowerCase().includes(text) ||
          game.Publisher.toString().toLowerCase().includes(text)
        );
      });
      this.myJson = stringFiltrada;
    },

    doAjax() {
      this.isLoading = true;
      // simulate AJAX
      setTimeout(() => {
        this.isLoading = false;
      }, 5000);
    },
    onCancel() {
      console.log("User cancelled the loader.");
    },

    onChangePage(pageOfItems) {
      // update page of items
      this.pageOfItems = pageOfItems;
    },

    modalVideo(game) {
      let modal = `${game.Rank}`.getAttribute("src");

      return `#gameModal${game.Rank}`
        .on("hide.bs.modal", function () {
          `${game.Rank}`.getAttribute("src", "");
        })(`##gameModal${game.Rank}`)
        .on("show.bs.modal", function () {
          `#${game.Rank}`.getAttribute("src", modal);
        });
    },

    closeModalVideo() {
      location.reload();
      return false;
    },
  },
  mounted() {
    this.myTopFive = this.myJson.slice(Math.max(myJson.length - 5, 1));
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Roboto;
}

body {
  color: #444;
  font-family: sans-serif;
  position: relative;
  border-top: 10px solid #0070c0;
}

.container {
  width: 1200px;
  margin-left: auto;
  margin-right: auto;
  margin-top: -60px;
  /* position: absolute; */
}

.main-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: #f7f7f7;
  padding: 10px 10px;
  height: 90px;
  top: 0;
  width: 1158px;
}

.searchbar-and-btn {
  margin-right: -10px;
  width: 300px;
}

.searchbar {
  margin-top: 10px;
  /* border-radius: 50%; */
  border: none;
  height: 30px;
  width: 85%;
  background-color: white;
  padding-left: 15px;
}

.btn-search {
  background-color: white;
  border: none;
  border-radius: 8%;
  height: 17px;
  width: 15px;
  margin-left: -25px;
  cursor: pointer;
}

nav {
  font-size: 12px;
}

.links {
  margin-top: 10px;
  display: flex;
  align-items: center;
  /* gap: 5px; */
  /* font-weight: bold; */
}

a {
  font-size: 10px;
}

.header-logo {
  width: 4%;
  height: auto;
  margin-left: 1%;
}

aside {
  background-color: #f7f7f7;
  border-top: 5px solid #0070c0;
  border-bottom: 5px solid #0070c0;
  padding: 30px 30px;
  width: 230px;
  margin-top: 15px;
}

h1,
h2,
h3 {
  color: #0070c0;
}

h1 {
  font-size: 26px;
  text-transform: uppercase;
  /* font-style: italic; */
  width: 507.234px;
  margin-right: 20%;
  justify-items: left;
  font-weight: bold;
}

h2 {
  font-size: 30px;
  margin-bottom: 30px;
  font-weight: bold;
}

h3 {
  font-size: 15px;
}

h4 {
  font-size: 15;
  text-transform: uppercase;
  text-align: center;
  margin-bottom: 10px;
  color: #0070c0;
  font-weight: bold;
  text-shadow: 0 3.2rem 6.4rem rgba(0, 0, 0, 0.06);
}
/* 
ul {
  margin-left: 50px;
  margin-bottom: 20px;
} */

li {
  float: left;
  font-size: 20px;
  margin-bottom: 10px;
}

li:last-child {
  margin-bottom: 0;
}

.related-list {
  list-style: none;
  margin-left: 0;
  flex-direction: column;
  display: flex;
  align-items: center;
}

a:link {
  color: #0070c0;
  text-decoration: none;
  font-size: 15px;
  margin-left: 7px;
}
a:visited {
  /* color: #777; */
  color: #0070c0;
}

a:hover {
  /* color: orangered;
  font-weight: bold; */
  text-decoration: underline #0070c0;
}

nav a:link {
  margin-right: 30px;
  display: inline-block;
}

nav a:link:last-child {
  margin-right: 0;
}

h2 {
  position: relative;
  padding-left: 0;
}

.main-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.related-list {
  display: flex;
  align-items: center;
  gap: 20px;
  margin-bottom: 10px;
}

.related-game {
  margin-bottom: -50;
  font-size: 14px;
  font-weight: normal;
  font-style: italic;
  display: block;
}

.container {
  display: grid;
  grid-template-columns: 850px 300px;
  column-gap: 75px;
  row-gap: 60px;
  align-items: start;
}

.main-header {
  /* grid-column: 1 / span 2; */
  grid-column: 1 / -1;
}

.carousel-indicators {
  margin-left: -15px;
}
.carousel {
  margin-top: 5px;
  margin-right: 0;
  justify-content: center;
  display: flex;
  align-items: center;
  transition: width 2s linear 1s;
}

.sld-img {
  width: 925px;
  height: auto;
}

.carousel-inner {
  width: 925px;
  height: auto;
  background-color: white;
  border: none;
}

.carousel-control {
  width: 50px;
}

.wrapper {
  display: grid;
  grid-column-start: 1;
  grid-column-end: 3;
  grid-template-columns: 268px 268px 268px;
  grid-column-start: span 2;
  gap: 25px 10px;
  grid-template-rows: auto;
  list-style-type: none;
  width: 825px;
  margin-left: -48px;
  margin-right: auto;
  margin-top: 0px;
  float: left;
  /* width: 100%; */
  position: absolute;
  margin-bottom: auto;
}

.itemGame {
  font-size: 10px;
  box-shadow: 0 2.4rem 4.8rem rgba(0, 0, 0, 0.075);
  border-radius: 11px;
  overflow: hidden;
  transition: all 0.4s;
  text-align: left;
  padding: 30px 10px 35px 0px;
  list-style: none;
  margin-left: 30px;
  position: relative;
  cursor: pointer;
  margin-bottom: 40px;
  padding-left: 10px;
  width: 240px;
  height: 300px;
}

.pagination {
  position: relative;
  justify-self: center;
  margin-left: 32%;
  font-weight: 100;
}

.itemGame:hover {
  transform: translateY(-1.2rem);
  box-shadow: 0 3.2rem 6.4rem rgba(0, 0, 0, 0.06);
}

.tag {
  display: flex;
  position: absolute;
  box-shadow: 0 2.4rem 4.8rem rgba(0, 0, 0, 0.075);
  border-radius: 11px;
  overflow: hidden;
  transition: all 0.4s;
  margin-top: -18px;
  justify-self: flex-start;
  /* margin-bottom: 55px; */
  gap: 0.4rem;
  background-color: #0070c0;
  display: inline-block;
  padding: 0.4rem 0.8rem;
  font-size: 10px;
  text-transform: uppercase;
  color: #f2f2f2;
  border-radius: 100px;
  font-weight: 600;
}

article {
  width: 850px;
  margin-left: 0;
  margin-right: auto;
  margin-top: -1000px;
  margin-bottom: 150px;
}

.tag-name {
  font-size: 12px;
  font-weight: bold;
  display: inline-block;
  width: auto;
  padding: 2px;
}

.paginationjs-pages {
  display: block;
  /* margin-left: 250px; */
  /* margin-right: 412.5px; */
  width: 385px;
  margin-top: 1200px;
  margin-bottom: 200px;
  position: relative;
}

.J-paginationjs-page {
  background-color: black;
  border-style: none;
}
.teste {
  border: none;
}

.top-link {
  margin-bottom: 0;
  font-size: 14px;
  font-weight: normal;
  font-style: italic;
  display: block;
  font-size: 1px;
}

.modal-title {
  /* font-style: italic; */
  font-size: 25px;
  text-shadow: 0 3.2rem 6.4rem rgba(0, 0, 0, 0.06);
  font-weight: bold;
  color: #0070c0;
}

.modal {
  box-shadow: 0 2.4rem 4.8rem rgba(0, 0, 0, 0.075);
  border-radius: 80px;
  overflow: hidden;
}

.bs-example {
  margin: 20px;
}

.modal-content iframe {
  margin: 0 auto;
  display: block;
}

.modal-dialog {
  margin-left: auto;
  margin-right: auto;
  margin-top: 9%;
  margin-bottom: auto;
  /* width: 8em  */
}

.modal .modal-content {
  padding: 10px 10px 10px 5px;
  -webkit-animation-name: modal-animation;
  -webkit-animation-duration: 0.5s;
  animation-name: modal-animation;
  animation-duration: 0.5s;
}

.top-link {
  width: 100px;
  margin-right: 0px;
}

.thirdHeader {
  text-align: center;
  margin-top: 80px;
  margin-bottom: 20px;
}

@import url(https://fonts.googleapis.com/css?family=Roboto:400,500,300,700);

.footer-distributed {
  background-color: #fff;
  box-shadow: 0 1px 1px 0 rgba(0, 0, 0, 0.12);
  box-sizing: border-box;
  width: 100%;
  text-align: left;
  font: normal 16px sans-serif;
  padding: 45px 50px;
  margin-top: 100px;
  height: 150px;
  border-style: double;
  border-top-width: 0.5px;
  border-top-style: solid;
  border-color: #0070c0;
  border-right: none;
  border-left: none;
  border-bottom: none;
}

.footer-distributed .footer-left p {
  color: #8f9296;
  font-size: 14px;
  margin: 0;
}
/* Footer links */

.footer-distributed p.footer-links {
  font-size: 18px;
  font-weight: bold;
  color: #8f9296;
  margin: 0 0 10px;
  padding: 0;
  transition: ease 0.25s;
}

.footer-distributed .footer-right {
  float: right;
  margin-top: 6px;
  max-width: 180px;
}

.footer-distributed .footer-right a {
  display: inline-block;
  width: 35px;
  height: 35px;
  background-color: #0070c0;
  border-radius: 2px;
  font-size: 20px;
  color: #ffffff;
  text-align: center;
  line-height: 35px;
  margin-left: 3px;
  transition: all 0.25s;
}
/* Media Queries */

@media (max-width: 600px) {
  .footer-distributed .footer-left,
  .footer-distributed .footer-right {
    text-align: center;
  }
  .footer-distributed .footer-right {
    float: none;
    margin: 0 auto 20px;
  }
  .footer-distributed .footer-left p.footer-links {
    line-height: 1.8;
  }
}
</style>
