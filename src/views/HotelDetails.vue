<template>
  <div>
    <Navbar />
    <!-- <div id="group">
      <button class="btn btn-light">
        <a href="#Activities">Activities</a>
      </button>
      <button class="btn btn-light">
        <a href=" #Inclusions"> Inclusions</a>
      </button>
      <button class="btn btn-light">
        <a href="#Exclusions">Exclusions</a>
      </button>
      <button class="btn btn-light"><a href="#Price">Price</a></button>
      <button class="btn btn-light">
        <a href="#Instructions">Instructions</a>
      </button>
    </div> -->
    <section id="content">
      <div class="content-wrap">
        <div class="container clearfix">
          <div class="postcontent nobottommargin clearfix" style="width: 800px">
            <div v-for="hotel in hotels" :key="hotel.id">
              <div v-if="this.id == hotel.id">
                <div id="posts" style="text-align: left">
                  <div class="entry clearfix">
                    <img
                      :src="hotel.img1"
                      style="height: 500px; width: 800px"
                      alt=""
                    />
                    <div id="social">
                      <button class="btn btnF">
                        <a
                          href="https://www.facebook.com/travelforing/"
                          target="_blank"
                          ><i class="fab fa-facebook"></i
                        ></a>
                      </button>
                      <button class="btn btnE">
                        <a
                          href="mailto:travelforing@gmail.com?subject=subject text"
                          ><i class="far fa-envelope"></i
                        ></a>
                      </button>
                      <button class="btn btnI">
                        <a
                          href="https://instagram.com/foringer_dol?utm_medium=copy_link"
                          target="_blank"
                          ><i class="fab fa-instagram"></i
                        ></a>
                      </button>
                      <button class="btn btnP">
                        <a
                          href="https://youtube.com/channel/UC-CGAoKw4Cf4xJt8kT8B-ZQ"
                          target="_blank"
                          ><i class="fab fa-youtube"></i
                        ></a>
                      </button>
                      <button class="btn btnT">
                        <a href=""><i class="fab fa-twitter"></i></a>
                      </button>
                      <button class="btn btnW">
                        <a href=""><i class="fab fa-whatsapp"></i></a>
                      </button>
                    </div>
                    <div class="entry-title" v-if="hotel.name">
                      <h2>
                        <a href="#">{{ hotel.name }}</a>
                      </h2>
                    </div>
                    <div
                      class="entry-content short-description hotel"
                      v-if="hotel.location"
                    >
                      <a
                        href="#"
                        class="icon-map-marker2"
                        style="color: #999999"
                        >{{ " " + hotel.location }}</a
                      >
                    </div>
                  </div>
                  <div
                    class="entry clearfix"
                    id="description"
                    v-if="hotel.description"
                  >
                    <div class="entry-content description">
                      <p>{{ hotel.description }}</p>
                    </div>
                  </div>
                  <div id="images">
                    <vueper-slides
                      :bullets="true"
                      :fixed-height="true"
                      fade
                      autoplay
                    >
                      <vueper-slide
                        v-for="slide in hotel.slider_img"
                        :key="slide"
                        :image="slide.img"
                      />
                    </vueper-slides>
                  </div>
                  <div
                    class="entry-content"
                    id="features"
                    v-if="hotel.features"
                  >
                    <h4>Features:</h4>
                    <div v-for="feat in hotel.features" :key="feat">
                      <p>
                        <i class="fas fa-vector-square"></i>{{ feat.feature }}
                      </p>
                    </div>
                  </div>
                  <div class="entry-content">
                    <div class="price-details">
                      <h4 v-if="hotel.package_price">Price:</h4>
                      <table>
                        <tr>
                          <td
                            v-for="(pacprice, i) in hotel.package_price"
                            :key="i"
                            id="price-D"
                          >
                            <div class="price-color">
                              <div>
                                <input
                                  type="radio"
                                  @click="booknow"
                                  name="number"
                                  :value="{
                                    price: pacprice.priceD,
                                    package: pacprice.room_type,
                                  }"
                                  v-model="picked"
                                />
                              </div>

                              <div>
                                {{ pacprice.room_type }}
                              </div>

                              <div>
                                {{ pacprice.priceD }}
                              </div>
                            </div>
                          </td>
                        </tr>
                      </table>
                    </div>

                    <div class="product clearfix" v-if="this.id == hotel.id">
                      <div v-if="book">
                        <div class="smallevent" id="totalprice-smallevent">
                          <div>
                            <img
                              style="width: 200px; height: 200px"
                              :src="hotel.img1"
                              alt=""
                            />
                          </div>
                          <div class="smalleventBottom">
                            <h4>
                              {{ hotel.name }}
                            </h4>
                            <p>৳{{ picked.price }}</p>
                            <p>Package: {{ picked.package }}</p>
                            <p class="pb-3">
                              <i id="map-icon" class="icon-map-marker2 pr-2"></i
                              >{{ hotel.location }}
                            </p>

                            <button
                              class="button button-3d nomargin"
                              @click="toCheckout(hotel)"
                            >
                              Book Now
                            </button>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                  <div class="entry-content product-price pb-5">
                    <div v-if="hotel.price"><h4>Note:</h4></div>
                    <div>
                      <ins v-if="hotel.price_details">{{
                        hotel.price_details
                      }}</ins>
                    </div>
                  </div>
                  <div class="entry-image" id="fb_group">
                    <a
                      href="https://www.facebook.com/groups/foringerdol/"
                      class="entry-link"
                      target="_blank"
                    >
                      Join Our Facebook Group
                      <span>https://www.facebook.com/groups/foringerdol/</span>
                    </a>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="smalldiv">
            <div v-for="hotel in hotels" :key="hotel.id">
              <div class="product clearfix" v-if="this.id == hotel.id">
                <div class="smalleventTop">
                  <div class="product-image">
                    <a href=""
                      ><img
                        style="width: 270px; height: 220px"
                        :src="hotel.img1"
                        alt=""
                    /></a>
                    <a href=""
                      ><img
                        style="width: 270px; height: 220px"
                        :src="hotel.img2"
                        alt=""
                    /></a>
                  </div>
                  <div id="smallevent-details">
                    <div class="product-title">
                      <h4 class="pt-3">
                        {{ hotel.name }}
                      </h4>
                      <h3>৳ {{ hotel.price }}</h3>
                    </div>
                    <a
                      href="#price"
                      class="button button-3d nomargin"
                      id="booknow"
                    >
                      Book Now
                    </a>
                  </div>
                </div>
              </div>
            </div>
            <div class="sidebar nobottommargin col_last clearfix">
              <div class="sidebar-widgets-wrap">
                <div class="widget clearfix" id="sidebar-tabs">
                  <div class="tabs nobottommargin clearfix" id="events">
                    <h3 class="pb-3">Related Hotels</h3>
                    <div class="tab-content clearfix" id="tabs-1">
                      <div id="popular-post-list-sidebar">
                        <div
                          class="spost clearfix"
                          v-for="hotel in hotels.slice(0, 6)"
                          :key="hotel"
                        >
                          <div v-if="this.area === hotel.area">
                            <router-link
                              :to="{
                                name: 'HotelDetails',
                                params: { id: hotel.id },
                              }"
                            >
                              <div class="entry-image">
                                <a href="#" class="nobg"
                                  ><img :src="hotel.img1" alt=""
                                /></a>
                              </div>
                              <div class="entry-title" id="hotel-name">
                                <h4>
                                  {{ hotel.name }}
                                </h4>
                              </div>
                            </router-link>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div class="clearfix">
                  <h3>Tag Cloud</h3>
                  <div class="tagcloud" id="tags">
                    <a href="#description">Description</a>
                    <a href="#images">Images</a>
                    <a href="#features">Features</a>
                    <a href="#price">Price</a>
                    <a href="#fb_group">Facebook Group</a>
                    <a href="#social">Social Links</a>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <Footer />
  </div>
</template>

<script>
import { ErrorMessage, Field, Form } from "vee-validate";
import { VueperSlide, VueperSlides } from "vueperslides";
import "vueperslides/dist/vueperslides.css";
import { mapState } from "vuex";
import Footer from "../components/Footer1.vue";
import Navbar from "../components/Navbar.vue";
export default {
  props: ["id", "area"],
  computed: {
    ...mapState("productbox", ["hotels"]),
  },
  data() {
    return {
      user: {
        name: "",
        email: "",
        review: "",
      },
      book: false,
      picked: "",
    };
  },
  methods: {
    onSubmit() {
      console.log(this.email);
    },
    isRequired(value) {
      return value ? true : "This field is required";
    },
    booknow() {
      this.book = true;
    },
    toCheckout(hotel) {
      this.$router.push({
        name: "Checkout",
        query: {
          type: "hotels",
          p: this.picked.price,
          pack: this.picked.package,
        },
      });
      this.$store.dispatch("productbox/addhotel", hotel);
      console.log(hotel);
      console.log(this.picked.price);
    },
  },
  components: {
    Navbar,
    Footer,
    VueperSlides,
    VueperSlide,
    Field,
    Form,
    ErrorMessage,
  },
};
</script>

<style scoped>
.vueperslides--fixed-height {
  height: 65vh;
  width: 800px;
}
.container {
  display: flex;
}
.content-wrap {
  padding: 0;
}
.entry-title {
  margin-top: 5%;
}
.entry-title h4 {
  text-align: center;
}
.entry {
  margin: 0;
  padding: 0;
}
.entry-content p {
  margin: 0;
  padding: 0.9% 0;
}
.entry-content h4 {
  margin: 0;
}
.hotel {
  display: flex;
  align-items: flex-end;
}
.hotel a {
  font-size: 1.6rem;
  margin-top: -12%;
}
#hotel-name {
  padding-top: 5%;
}
.description p {
  padding-bottom: 5%;
}
.price {
  padding-bottom: 5%;
  display: flex;
  align-items: flex-end;
}
.price-color {
  background-color: #fafaf2;
  padding: 1% 3%;
}
#price-D {
  width: 150px;
}
#price-D div {
  padding: 5% 10%;
}

.entry-content i {
  font-size: 0.9rem;
  padding-right: 1%;
}
.product-price {
  margin: 0;
  padding: 0;
}
#social .btn {
  padding: 0 6%;
  margin: 0 0.5%;
}
#social .btn:hover {
  background-color: #979797;
}
#social {
  padding: 1% 0;
  margin-right: -3%;
}
#social .btnF {
  background-color: #4267b2;
}
#social .btnW {
  background-color: #25d366;
}
#social .btnT {
  background-color: #55acee;
}
#social .btnE {
  background-color: #ea4335;
}
#social .btnI {
  background-color: #d43e7d;
}
#social .btnP {
  background-color: #cb2027;
}
#social a {
  padding: 2% 15%;
  font-size: 2.5rem;
  color: #fff;
}
#content {
  margin-top: 2%;
  margin-bottom: 0%;
}
.smallevent {
  width: 600px;
  padding: 0 5% 0 0;
  background-color: #fafaf2;
}
.entry-title h4 {
  text-align: center;
}
.product-title h3 {
  margin-top: -10%;
}
#booknow {
  color: #ffffff;
}
#totalprice-smallevent {
  display: flex;
}
.smallevent-details p,
h5,
h3 {
  margin: 0;
}
.smallevent-details {
  padding-left: 5%;
}
.smalleventBottom {
  padding-top: 2%;
  padding-left: 3%;
}
.smalleventBottom p,
#map-icon {
  margin: 0;
  font-size: 1.5rem;
}
#sidebar-tabs {
  margin-bottom: 20%;
}
#sidebar-tabs h3 {
  margin-top: 20%;
  margin-bottom: 10%;
}
#tags {
  padding-top: 7%;
}
</style>
