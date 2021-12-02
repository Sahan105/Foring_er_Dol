<template>
  <div class="product-box">
    <div class="section notopmargin notopborder" id="section">
      <div class="container clearfix">
        <div class="heading-block center nomargin" id="heading">
          <h3>Featured Events</h3>
          <p>Call us on: 01880089100 or Mail us on: travelforing@gmail.com</p>
        </div>
      </div>
    </div>
    <Carousel :itemsToShow="4" :itemsToScroll="2">
      <Slide v-for="event in events" :key="event" class="productB">
        <div class="product clearfix">
          <router-link :to="{ name: 'EventDetails', params: { id: event.id } }">
            <div class="product-image">
              <a href=""
                ><img
                  style="width: 370px; height: 300px"
                  :src="event.img1"
                  alt=""
              /></a>
              <a href=""
                ><img
                  style="width: 370px; height: 300px"
                  :src="event.img2"
                  alt=""
              /></a>
              <div class="product-overlay"> 
                <!-- <router-link
                :to="{ name: 'EventDetails', params: { id: event.id } }"
                ><i class="icon-zoom-in"></i><span></span>
              </router-link> -->
              </div>
            </div>
          </router-link>
          <router-link :to="{ name: 'EventDetails', params: { id: event.id } }">
            <div id="text">
              <div class="product-title pt-2">
                <h4>
                  <a href="">{{ event.name }}</a>
                </h4>
              </div>
              <div class="product-price">
                <ins>৳ {{ event.price }}</ins>
              </div>
            </div>
          </router-link>
        </div>
      </Slide>
      <template #addons>
        <Navigation />
      </template>
    </Carousel>
  </div>
</template>

<script>
import { mapState } from "vuex";
import { defineComponent } from "vue";
import { Carousel, Navigation, Slide } from "vue3-carousel";

import "vue3-carousel/dist/carousel.css";

export default defineComponent({
  name: "Basic",
  components: {
    Carousel,
    Slide,
    Navigation,
  },
  methods: {
    // toCheckout(event) {
    //   this.$router.push({ name: "Checkout", query: { type: "events" } });
    //   this.$store.dispatch("productbox/addevent", event);
    //   console.log(event);
    // },
  },
  computed: {
    ...mapState("productbox", ["events"]),
  },
});
</script>

<style scoped>
.carousel__item {
  width: 100%;
  background-color: #1c3df6;
  color: #ffecec;
  font-size: 20px;
  border-radius: 8px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.carousel__slide {
  background-color: #f9f9f9;
}
.section {
  margin: 0;
}
.item-quick-view {
  padding: 0 70%;
  border: 0.5px solid #ddd;
  background-color: #fafafa;
}
.carousel__prev,
.carousel__next {
  box-sizing: content-box;
  border: 5px solid white;
}
.productB {
  padding: 0 1.5%;
}
#text {
  text-align: left;
  padding: 0 0 13% 0;
}

.clearfix {
  margin: 0;
}
.product-price {
  margin: 0;
}
.product-title h4 {
  margin: 0;
  width: 300px;
}

.container {
  margin: 0;
  padding: 0;
}
.content-wrap {
  padding: 0;
}

.add-to-cart i,
.item-quick-view i {
  font-size: 3rem;
  color: #5a5a5a;
}
.product-box {
  padding: 0 5%;
  margin-top: 0%;
}
.add-to-cart:hover,
.item-quick-view:hover {
  background-color: #ddd;
  color: #bdbdbd;
}
#section {
  margin: 0;
  padding-top: 2%;
  padding-bottom: 2%;
}
#heading {
  padding-left: 20%;
}
</style>
