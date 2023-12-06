<template>
  <div>
    <div class="logo"><img :src="marvelLogo" alt="" /></div>
    <CustomCard />
  </div>
</template>

<script>
import marvelLogo from "./assets/marvelLogo.png";
import CustomCard from "./components/CustomCard.vue";
export default {
  components: { CustomCard },
  data() {
    return {
      marvelLogo: marvelLogo,
    };
  },
};
</script>

<style scoped>
.logo {
  display: flex;
  justify-content: center;
  align-items: center;
  background: transparent;
  margin-top: 100px;
  padding: 0;
  z-index: -999999;
}

.logo img {
  width: 300px;
}

@media (max-width: 650px) {

  .logo {
    margin-top: 0px;
  }
  .logo img {
    width: 150px;
  }
}
</style>
