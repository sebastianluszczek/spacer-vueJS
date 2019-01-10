<template>
  <div class="search-wrapper">
    <div class="search">
      <input type="text" name="search" v-model="searchValue" v-on:input="handleInput">
    </div>
  </div>
</template>

<script>
import axios from "axios";
import debounce from "lodash.debounce";

const API = "https://images-api.nasa.gov/search";

export default {
  name: "SearchInput",
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
.search-wrapper {
  margin-top: 50px;
}
.search-wrapper .search {
  display: flex;
  flex-direction: column;
  width: 300px;
}

input {
  height: 30px;
  border: 0;
  border-bottom: 2px solid black;
  background: none;
}
</style>


