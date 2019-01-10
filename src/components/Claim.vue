<template>
  <div class="claim-wrapper">
    <h1 class="claim">SPACER</h1>
    <p
      class="subclaim"
    >Begin your journey through our amazing galaxy and discover places you never even heard of.</p>
    <p class="subclaim">Type anything space-related to start</p>
  </div>
</template>
<script>
export default {
  name: "Claim",
  data() {
    return {};
  }
};
</script>
<style>
.claim-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;

  color: #fff;
}
.claim {
  font-size: 50px;
}

.subclaim {
  font-size: 13px;
  margin: 20px 0 0 0;
}

@media (min-width: 768px) {
  .claim {
    font-size: 80px;
  }

  .subclaim {
    font-size: 17px;
    letter-spacing: 1px;
    width: 500px;
  }
}

@media (min-width: 1024px) {
  .claim {
    font-weight: 600;
  }
}
</style>


