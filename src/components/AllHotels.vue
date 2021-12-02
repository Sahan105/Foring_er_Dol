<template>
  <div class="hotels">
    <div class="section notopmargin notopborder" id="section">
      <div class="heading-block center nomargin">
        <h3>Hotels</h3>
        <p>Call us on: 01880089100 or Mail us on: travelforing@gmail.com</p>
      </div>
    </div>
    <div id="shop">
      <div v-for="hotel in hotels" :key="hotel" id="product">
        <HotelCart :hotel="hotel" />
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
import HotelCart from "../components/carts/HotelCart";
export default {
  computed: {
    ...mapState("productbox", ["hotels"]),
  },
  components: {
    HotelCart,
  },
};
</script>
<style scoped>
.hotels {
  margin-bottom: -2%;
}
#shop {
  padding: 4%;
  display: grid;
  /* width: 300px; */
  grid-template-columns: repeat(4, 1fr);
}
#section {
  margin: 0;
  padding-top: 2%;
  padding-bottom: 2%;
}
</style>
