<template>
  <div class="wrapper">
    <div class="search">
      <label for="search">Search</label>
      <input type="text" name="search" v-model="searchValue" v-on:input="handleInput">
    </div>
    <ul v-for="item in results" v-bind:key="item.data[0].nasa_id">
      <li>{{item.data[0].description}}</li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
import debounce from "lodash.debounce";

const API = "https://images-api.nasa.gov/search";
export default {
  name: "Search",
  data() {
    return {
      searchValue: "",
      results: []
    };
  },
  methods: {
    handleInput: debounce(function() {
      axios
        .get(`${API}?q=${this.searchValue}&media_type=image`)
        .then(response => {
          this.results = response.data.collection.items;
        })
        .catch(err => {
          console.log(err);
        });
    }, 500)
  }
};
</script>

<style>
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 0;
  padding: 30px;
  width: 100%;
}

.wrapper .search {
  display: flex;
  flex-direction: column;
  width: 300px;
}

label {
  font-family: Monserrat, sans-serif;
}

input {
  height: 30px;
  border: 0;
  border-bottom: 2px solid black;
}
</style>
