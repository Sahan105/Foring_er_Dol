<template>
  <div class="main-navbar">
    <div class="navbar" id="nav">
    <router-link :to="{ path: '/' }" class="image">
      <img
        alt="logo"
        src="../assets/images/icons/Foringer-Dol.png"
      />
    </router-link>
    <div class="main-nav">
      <router-link v-for="item in list" :key="item" :to="item.to">{{
        item.title
      }}</router-link>
    </div>
  </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
export default {
  name: "navbar",
  computed: {
    ...mapState("navbar", ["list"]),
  },
};
</script>

<style scoped>
* {
  padding: 0;
  margin: 0;
}
.main-navbar {
  width: 100%;
}
.image {
  margin-left: 2%;
}
.navbar img {
  height: 45px; 
  width: 190px;
}
#nav {
  width: 100%;
  padding: 0.8%;
}
.main-nav {
  margin-left: 20%;
  font-size: 1.8rem;
}
.main-nav a {
  color: #121413;
  padding: 2rem;
}
</style>
