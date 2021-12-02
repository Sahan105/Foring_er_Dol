<template>
  <div class="product-box">
    <div class="product">
      <router-link :to="{name: 'HotelDetails', params: { id: hotel.id, loc: hotel.location, area: hotel.area } }">
      <div class="product-image">
        <a href="#">
          <img style="width: 320px; height: 300px" :src="hotel.img1" alt="" />
        </a>
        <a href="#">
          <img style="width: 320px; height: 300px" :src="hotel.img2" alt="" />
        </a>
        <div class="product-overlay"></div>
      </div>
    </router-link>
    <div id="text">
      <div class="product-title">
        <h3>
          <router-link :to="{name: 'HotelDetails', params: { id: hotel.id, loc: hotel.location, area: hotel.area } }">{{ hotel.name }}</router-link>
        </h3>
      </div>
      <div class="product-price">
        <ins>৳ {{ hotel.price }}</ins>
      </div>
      <div>
        <a href="#" class="icon-map-marker2" style="color: #999999">{{" " + hotel.location}}</a>
      </div>
    </div>  
    </div>
  </div>
</template>

<script>
export default {
  props: ["hotel"],
  methods: {
    book() {
      localStorage.setItem("name", this.$props.hotel.name);
      localStorage.setItem("price", this.$props.hotel.price);
      localStorage.setItem("img", this.$props.hotel.img1);
    },
  },
};
</script>

<style scoped>
#text {
  text-align: left;
  padding-top: 1%;
}
.product-box {
  width: 320px;
  padding: 0%;
}
.product-price {
  margin: 0;
}
.product {
  padding-left: 10%;
  padding-bottom: 5%;
  padding-top: 5%;
}
</style>
