<template>
  <div class="item" :style="style"></div>
</template>

<script>
export default {
  name: "Item",
  props: {
    item: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      photo: this.item.links[0].href,
      title: this.item.data[0].titlem
    };
  },
  computed: {
    style() {
      return `background-image: url("${this.photo}")`;
    }
  }
};
</script>

<style>
.item {
  min-width: 80vw;
  height: 250px;
  background-repeat: no-repeat;
  background-position: 50%;
}

@media (min-width: 786px) {
  .item {
    min-width: 40vw;
  }
}

@media (min-width: 1024px) {
  .item {
    min-width: 25vw;
  }
}
</style>




