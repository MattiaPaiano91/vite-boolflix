<script>
import { data } from "../store.js";
export default {
  data() {
    return {
      data,
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
  },
  props: {
    resultMovie: Array,
    resultTV: Array,
  },
};
</script>

<template>
  <main>
    <div class="card-container m-5 " v-for="(elem, i) in resultMovie" :key="i">
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
        </ul>
      </div>
    </div>
    <div class="card-container  m-5" v-for="(series, j) in resultTV" :key="j">
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
        </ul>
      </div>
    </div>
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
  background-color: rgb(30, 30, 30);
  min-height: calc(100vh - 100px);
  .card-container {
    position: relative;
    width: 342px;
    height: 500px;
    &:hover .card {
      opacity: 0.5;
    }
    &:hover .card-information{
        display: flex;
        align-items: center;
    }
    .card-information {
      display: none;
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      font-size: 1.5rem;
      font-weight:500;
      color: white;
      img {
        width: 20px;
        height: 10px;
      }
    }
  }
}
</style>
