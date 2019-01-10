<template>
  <div class="wrapper">
    <Claim/>
    <SearchInput/>
  </div>
</template>

<script>
import Claim from "@/components/Claim";
import SearchInput from "@/components/SearchInput";

export default {
  name: "Search",
  data() {
    return {};
  },
  components: {
    Claim,
    SearchInput
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
  background-image: url("../assets/heroimage.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 80% 0;
}
</style>
