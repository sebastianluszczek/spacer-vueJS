<template>
  <div :class="[{ flexStart: step === 1 },'wrapper']">
    <transition name="slide">
      <img src="../assets/logo.svg" class="logo" v-if="step === 1">
    </transition>
    <transition name="fade">
      <HeroImage v-if="step === 0"/>
    </transition>
    <Claim v-if="step === 0"/>
    <SearchInput v-model="searchValue" @input="handleInput" :dark="step === 1"/>
    <div class="results" v-if="results && !loading && step === 1">
      <Item v-for="item in results" :item="item" :key="item.data[0].nasa_id"/>
    </div>
  </div>
</template>

<script>
import HeroImage from "@/components/HeroImage";
import Claim from "@/components/Claim";
import SearchInput from "@/components/SearchInput";
import Item from "@/components/Item";

import axios from "axios";
import debounce from "lodash.debounce";

const API = "https://images-api.nasa.gov/search";

export default {
  name: "Search",
  data() {
    return {
      loading: "false",
      step: 0,
      searchValue: "",
      results: []
    };
  },
  components: {
    Claim,
    SearchInput,
    HeroImage,
    Item
  },
  methods: {
    handleInput: debounce(function() {
      this.loading = true;
      axios
        .get(`${API}?q=${this.searchValue}&media_type=image`)
        .then(response => {
          this.results = response.data.collection.items;
          this.loading = false;
          this.step = 1;
          console.log(response);
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
  justify-content: center;
  margin: 0;
  padding: 30px;
  width: 100%;
  height: 100vh;
  position: relative;
}

.logo {
  position: absolute;
  top: 30px;
  left: 30px;
}

.wrapper.flexStart {
  justify-content: flex-start;
}

.wrapper .results {
  display: grid;
  grid-template-columns: 1fr;
  grid-gap: 20px;
  margin-top: 50px;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

.slide-enter-active,
.slide-leave-active {
  transition: margin-top 0.5s ease;
}
.slide-enter, .slide-leave-to /* .fade-leave-active below version 2.1.8 */ {
  margin-top: -50px;
}

@media (min-width: 786px) {
  .wrapper .results {
    grid-template-columns: 1fr 1fr;
  }
}
@media (min-width: 1024px) {
  .wrapper .results {
    grid-template-columns: 1fr 1fr 1fr;
  }
}
</style>
