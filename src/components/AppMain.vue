<script>
import { data } from "../store.js";
export default {
  data() {
    return {
      data,
      offcanvasCounter: null,
      offcanvasCounterTV: null,
    };
  },
  methods: {
    rightFlag(flag) {
      let flagUrl = "https://flagcdn.com/16x12/";
      if (flag == "en") {
        flagUrl += "gb-eng.png";
      } else if (flag == "ja") {
        flagUrl += "jp.png";
      } else {
        flagUrl += flag + ".png";
      }
      return flagUrl;
    },
    offcanvasInfo(i) {
      this.offcanvasCounter = i;
      this.offcanvasCounterTV = null;
    },
    offcanvasInfoTv(j) {
      this.offcanvasCounterTV = j;
      this.offcanvasCounter = null;
    },
    // le due funzioni impostano il valore del rispettivo counter al rispettivo indice di iterazione, in modo da poter usare la variabile
    // come indice per estrapolare determinati dati nella text interpolation. Impostano anche a null il valore dell'altra variabile in modo
    // che il v-if nell'offcanvas mi nasconda i dati indesiderati
  },
  props: {
    resultMovie: Array,
    resultTV: Array,
  },
};
</script>

<template>
  <div class="container-fluid text-bg-dark">
    <main class="pt-5">
      <!-- le card sono contentute in un tag <a> che scatena l'offcanvas -->

      <!-- sezione film -->
      <h2>Film</h2>

      <section class="section">
        <!-- card che contengono i film -->

        <div
          class="card-container m-3"
          v-for="(elem, i) in resultMovie"
          :key="i"
        >
          <a
            title="Scopri di più"
            data-bs-toggle="offcanvas"
            href="#offcanvasExample"
            role="button"
            aria-controls="offcanvasExample"
            @click="offcanvasInfo(i)"
            v-if="elem.backdrop_path"
          >
            <div class="card">
              <img
                :src="'https://image.tmdb.org/t/p/w300' + elem.poster_path"
                :alt="elem.original_title"
              />
            </div>
            <div class="card-information">
              <ul class="p-2">
                <li>Title:{{ elem.title }}</li>
                <li>Original title:{{ elem.original_title }}</li>
                <li>
                  <img
                    :src="rightFlag(elem.original_language)"
                    :alt="elem.original_language"
                  />
                </li>
                <li>vote:{{ elem.vote_average }}</li>
              </ul>
            </div>
          </a>
        </div>
      </section>

      <!-- sezione film -->
      <h2>serie TV</h2>

      <section class="section">

        <!-- card che contengono le Serie tv -->

        <div
          class="card-container m-3"
          v-for="(series, j) in resultTV"
          :key="j"
        >
          <a
            title="Scopri di più"
            data-bs-toggle="offcanvas"
            href="#offcanvasExample"
            role="button"
            aria-controls="offcanvasExample"
            @click="offcanvasInfoTv(j)"
            v-if="series.backdrop_path"
          >
            <div class="card">
              <img
                :src="'https://image.tmdb.org/t/p/w300' + series.poster_path"
                :alt="series.original_name"
              />
            </div>
            <div class="card-information">
              <ul class="p-2">
                <li>SERIES Title:{{ series.name }}</li>
                <li>Original title:{{ series.original_name }}</li>
                <li>
                  <img
                    :src="rightFlag(series.original_language)"
                    :alt="series.original_language"
                  />
                </li>
                <li>vote:{{ series.vote_average }}</li>
              </ul>
            </div>
          </a>
        </div>

      </section>

      <!-- 
        offcanvas che contiene le info del film/serie tv
       -->

      <div
        class="offcanvas offcanvas-start text-bg-dark"
        tabindex="-1"
        id="offcanvasExample"
        aria-labelledby="offcanvasExampleLabel"
      >
        <div class="offcanvas-header">
          <h3 class="offcanvas-title" id="offcanvasExampleLabel">overview</h3>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="offcanvas"
            aria-label="Close"
          ></button>
        </div>
        <div class="offcanvas-body text-bg-dark">
          <div class="text-white">
            <ul class="p-0">
              <li class="my-2">
                <h5 class="d-inline">Title:</h5>
                <p v-if="resultMovie && resultMovie[offcanvasCounter]">
                  {{ resultMovie[offcanvasCounter].title }}
                </p>
                <p v-if="resultTV && resultTV[offcanvasCounterTV]">
                  {{ resultTV[offcanvasCounterTV].name }}
                </p>
              </li>
              <li class="my-2">
                <h5 class="d-inline">Original Title:</h5>
                <p v-if="resultMovie && resultMovie[offcanvasCounter]">
                  {{ resultMovie[offcanvasCounter].original_title }}
                </p>
                <p v-if="resultTV && resultTV[offcanvasCounterTV]">
                  {{ resultTV[offcanvasCounterTV].original_name }}
                </p>
              </li>
              <li>
                <div v-if="resultMovie && resultMovie[offcanvasCounter]">
                  <img
                    :src="
                      'https://image.tmdb.org/t/p/w342' +
                      resultMovie[offcanvasCounter].poster_path
                    "
                    alt=""
                  />
                </div>

                <div v-if="resultTV && resultTV[offcanvasCounterTV]">
                  <img
                    :src="
                      'https://image.tmdb.org/t/p/w342' +
                      resultTV[offcanvasCounterTV].poster_path
                    "
                    alt=""
                  />
                </div>
              </li>
              <li class="mt-3 overview">
                <p v-if="resultMovie && resultMovie[offcanvasCounter]">
                  Overview: {{ resultMovie[offcanvasCounter].overview }}
                </p>
                <p v-if="resultTV && resultTV[offcanvasCounterTV]">
                  Overview: {{ resultTV[offcanvasCounterTV].overview }}
                </p>
              </li>
            </ul>
          </div>
        </div>
      </div>

      <!-- fine off canvas -->
    </main>
  </div>
</template>

<style lang="scss" scoped>
@use "../assets/scss/main.scss" as *;
img {
  border: none;
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.card {
  border: none;
  width: 342px;
  height: 500px;
}

li {
  list-style: none;
}
.offcanvas-title {
  color: red;
}
main {
  font-family: "Bebas Neue", sans-serif;
  width: 1200px;
  margin: 0 auto;
  min-height: calc(100vh - 100px);
  .section{
    display: flex;
    flex-wrap: wrap;
  }
  .card-container {
    position: relative;
    width: 342px;
    height: 500px;
    border: none;
    &:hover .card {
      opacity: 0.5;
    }
    &:hover .card-information {
      display: flex;
      align-items: center;
      cursor: pointer;
    }
    .card-information {
      display: none;
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      font-size: 1.2rem;
      font-weight: 500;
      color: white;
      img {
        width: 20px;
        height: 10px;
      }
      .overview {
        font-size: 1rem;
      }
    }
  }
}
</style>
