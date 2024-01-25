<script>
import { data } from "../store.js";
import axios from "axios";
export default {
  data() {
    return {
      data,
    };
  },
  methods: {},
};
</script>

<template>
  <header class="p-3">
    <div class="row">

      <div class="col-6 d-flex align-items-center logo-box">
          <h1 class="title">BOOLZAP</h1>
      </div>
          
      <div class="col-6 d-flex align-items-center justify-content-end ">
        <form class="h-75" @submit.prevent="$emit('userSearch')" action="">
          <div class="input-group mb-3 d-flex align-items-center">
            <input
              v-model="data.userSearch"
              type="text"
              class="form-control "
              placeholder="Cerca Serie tv o Film"
              aria-label="Recipient's username"
              aria-describedby="button-addon2"
            />
            <button
              class="btn btn-outline-secondary"
              type="submit"
              id="button-addon2"
            >
              Cerca
            </button>
          </div>
        </form>
      </div>

    </div>
  </header>
</template>

<style lang="scss" scoped>
@use "../assets/scss/main.scss" as *;

header {
    height: 100px;
    background-color: black;
    .row{
        height: 100%;
        .logo-box{
            height: 100%;
            line-height: 100px;
            .title{
                color: red;
                font-family: 'Bebas Neue', sans-serif;
                margin: auto 0;
            }
        }
      form {
       width: 400px;
      }
    }
    }
</style>
