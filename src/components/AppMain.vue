<script>
import { data } from "../store.js";
export default {
  data() {
    return {
      data,
      offcanvasCounter:null
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
    offcanvasInfo(i){
      this.offcanvasCounter = i
    }
  },
  props: {
    resultMovie: Array,
    resultTV: Array,
  },
};
</script>

<template>
  <main class="text-bg-dark">


    <!-- le card sono contentute in un tag <a> che scatena l'offcanvas -->

    <div class="card-container m-5" v-for="(elem, i) in resultMovie" :key="i">
      <a
        data-bs-toggle="offcanvas"
        href="#offcanvasExample"
        role="button"
        aria-controls="offcanvasExample"
        @click="offcanvasInfo(i)"
      >
        <div class="card">
          <img
            :src="'https://image.tmdb.org/t/p/w342' + elem.poster_path"
            :alt="elem.original_title"
          />
        </div>
        <div class="card-information">
          <ul>
            <li>Title:{{ elem.title }}</li>
            <li>Original title:{{ elem.original_title }}</li>
            <li>
              <img
                :src="rightFlag(elem.original_language)"
                :alt="elem.original_language"
              />
            </li>
            <li>vote:{{ elem.vote_average }}</li>
            <li class="overview">{{ elem.overview }}</li>
          </ul>
        </div>
      </a>
    </div>
    <div class="card-container m-5" v-for="(series, j) in resultTV" :key="j">
      <a
        data-bs-toggle="offcanvas"
        href="#offcanvasExample"
        role="button"
        aria-controls="offcanvasExample"
      >
      <div class="card">
        <img
          :src="'https://image.tmdb.org/t/p/w342' + series.poster_path"
          :alt="series.original_name"
        />
      </div>
      <div class="card-information">
        <ul>
          <li>SERIES Title:{{ series.name }}</li>
          <li>Original title:{{ series.original_name }}</li>
          <li>
            <img
              :src="rightFlag(series.original_language)"
              :alt="series.original_language"
            />
          </li>
          <li>vote:{{ series.vote_average }}</li>
          <li class="overview">{{ series.overview }}</li>
        </ul>
      </div>
      </a>
    </div>
        <!-- offcanvas che contiene le info del film/serie tv -->
    <div
      class="offcanvas offcanvas-start text-bg-dark "
      tabindex="-1"
      id="offcanvasExample"
      aria-labelledby="offcanvasExampleLabel"
    >
      <div class="offcanvas-header">
        <h5 class="offcanvas-title" id="offcanvasExampleLabel">Offcanvas</h5>
        <button
          type="button"
          class="btn-close"
          data-bs-dismiss="offcanvas"
          aria-label="Close"
        ></button>
      </div>
      <div class="offcanvas-body text-bg-dark ">
        <div class="text-white" v-if="resultMovie && resultMovie[offcanvasCounter]">
          {{ resultMovie[offcanvasCounter].original_title }}
        </div>
        <div class="dropdown mt-3">
          <button
            class="btn btn-secondary dropdown-toggle"
            type="button"
            data-bs-toggle="dropdown"
          >
            Dropdown button
          </button>
          <ul class="dropdown-menu">
            <li><a class="dropdown-item" href="#">Action</a></li>
            <li><a class="dropdown-item" href="#">Another action</a></li>
            <li><a class="dropdown-item" href="#">Something else here</a></li>
          </ul>
        </div>
      </div>
    </div>
    <!-- fine off canvas -->
  </main>
</template>

<style lang="scss" scoped>
@use "../assets/scss/main.scss" as *;
li {
  list-style: none;
}

main {
  font-family: "Bebas Neue", sans-serif;
  display: flex;
  flex-wrap: wrap;
  
  min-height: calc(100vh - 100px);
  .card-container {
    position: relative;
    width: 342px;
    height: 500px;
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
      font-size: 1.5rem;
      font-weight: 500;
      color: white;
      padding-right: 15px;
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
