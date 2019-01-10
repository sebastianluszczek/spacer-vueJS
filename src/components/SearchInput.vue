<template>
  <div class="search-wrapper">
    <div class="search">
      <input type="text" name="search" :class="{dark}" :value="value" @input="handleChange">
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchInput",
  data() {
    return {};
  },
  props: {
    value: {
      type: String,
      required: true
    },
    dark: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    handleChange(e) {
      this.$emit("input", e.target.value);
    }
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
  color: #fff;
  border-bottom: 2px solid;
  text-align: center;
  font-size: 18px;
  font-weight: 300;
  background: none;
  transition: box-shadow 0.5s;
}

input:focus {
  outline: none;
  box-shadow: 0 10px 20px -8px rgba(255, 255, 255, 0.4);
}

.dark {
  color: #1e3d4a;
}

.dark:focus {
  outline: none;
  box-shadow: 0 10px 20px -8px rgba(#1e3d4a, 0.4);
}

@media (min-width: 1024px) {
  input {
    font-weight: 400;
    font-size: 20px;
  }
}
</style>


