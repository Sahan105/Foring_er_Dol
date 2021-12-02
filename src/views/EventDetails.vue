<template>
  <div id="eventdetails">
    <Navbar />
    <!-- <div id="group">
      <button class="btn" id="btn">
        <a href="#Activities">Activities</a>
      </button>
      <button class="btn" id="btn">
        <a href=" #Inclusions"> Inclusions</a>
      </button>
      <button class="btn" id="btn">
        <a href="#Exclusions">Exclusions</a>
      </button>
      <button class="btn" id="btn"><a href="#Price">Price</a></button>
      <button class="btn" id="btn">
        <a href="#Instructions">Instructions</a>
      </button>
    </div> -->
    <section id="content">
      <div class="content-wrap">
        <div class="container clearfix">
          <div class="postcontent nobottommargin clearfix">
            <div v-for="event in events" :key="event.id">
              <div v-if="this.id == event.id" class="evntDetails">
                <div id="posts" style="text-align: left">
                  <div class="entry clearfix">
                    <img
                      :src="event.img1"
                      alt=""
                      style="height: 500px; width: 800px"
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
                          target="_blank"
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
                    <div class="entry-title">
                      <h2>
                        <a href="#">{{ event.name }}</a>
                      </h2>
                    </div>
                    <ul class="entry-meta clearfix">
                      <li v-if="event.date">
                        <i class="icon-calendar3"></i>{{ event.date }}
                      </li>
                      <li>
                        <a href="#"><i class="icon-user"></i> admin</a>
                      </li>
                      <li>
                        <a href="#"><i class="icon-camera-retro"></i></a>
                      </li>
                    </ul>
                    <div class="entry-content">
                      <p>{{ event.short_description }}</p>
                    </div>
                    <div class="entry-content">
                      <h4 v-if="event.event_duration">
                        Event Duration: {{ event.event_duration }}
                      </h4>
                    </div>
                    <div class="entry-content description" id="description">
                      <p>{{ event.description }}</p>
                    </div>
                    <div id="images">
                      <vueper-slides
                        :bullets="true"
                        :fixed-height="true"
                        fade
                        autoplay
                      >
                        <vueper-slide
                          v-for="slide in event.slider_img"
                          :key="slide"
                          :image="slide.img"
                        />
                      </vueper-slides>
                    </div>
                    <div class="entry-content hotel">
                      <div><h4 v-if="event.hotel">Hotel:</h4></div>
                      <div>{{ event.hotel }}</div>
                    </div>
                    <div class="entry-content" id="activities">
                      <h4 v-if="event.activities">Activities:</h4>
                      <div v-for="activity in event.activities" :key="activity">
                        <p>{{ activity.title }}: {{ activity.activity }}</p>
                      </div>
                    </div>
                    <div class="entry-content" id="inclusions">
                      <h4>Inclusions:</h4>
                      <div
                        v-for="inclusion in event.inclusions"
                        :key="inclusion"
                      >
                        <p>
                          <i class="fas fa-vector-square"></i
                          >{{ inclusion.inc }}
                        </p>
                      </div>
                    </div>
                    <div class="entry-content" id="exclusions">
                      <h4>Exclusions:</h4>
                      <div
                        v-for="exclusion in event.exclusions"
                        :key="exclusion"
                      >
                        <p>
                          <i class="fas fa-vector-square"></i
                          >{{ exclusion.exc }}
                        </p>
                      </div>
                    </div>
                    <div class="entry-content price" id="instructions">
                      <h4>Instructions:</h4>
                      <div v-for="pol in event.Policy" :key="pol">
                        <p>
                          <i class="fas fa-vector-square"></i>{{ pol.policy }}
                        </p>
                      </div>
                    </div>
                    <div class="entry-content">
                      <div class="price-details" id="price">
                        <h4 v-if="event.package_price">Price:</h4>
                        <table>
                          <tr>
                            <td
                              id="price-D"
                              v-for="(pacprice, i) in event.package_price"
                              :key="i"
                            >
                              <div class="price-color">
                                <div>
                                  <input
                                    type="radio"
                                    @click="booknow"
                                    name="number"
                                    :value="{
                                      price: pacprice.priceD,
                                      package: pacprice.person,
                                    }"
                                    v-model="picked"
                                  />
                                </div>
                                <div>
                                  {{ pacprice.person }}
                                </div>
                                <div>{{ pacprice.priceD }}</div>
                              </div>
                            </td>
                          </tr>
                        </table>
                      </div>

                      <div class="product clearfix" v-if="this.id == event.id">
                        <div v-if="book">
                          <div id="totalprice-smallevent" class="booking">
                            <div>
                              <img
                                style="width: 200px; height: 200px"
                                :src="event.img1"
                                alt=""
                              />
                            </div>
                            <div class="smallevent-details">
                              <h4>
                                {{ event.name }}
                              </h4>
                              <p>৳{{ picked.price }}</p>
                              <p>Package: {{ picked.package }}</p>
                              <p class="pb-3">
                                <i
                                  id="map-icon"
                                  class="icon-map-marker2 pr-2"
                                ></i
                                >{{ event.location }}
                              </p>

                              <button
                                class="button button-3d nomargin"
                                @click="toCheckout(event)"
                              >
                                Book Now
                              </button>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                    <div id="fb_group">
                      <a
                        href="https://www.facebook.com/groups/foringerdol/"
                        class="entry-link"
                        target="_blank"
                      >
                        Join Our Facebook Group
                        <span
                          >https://www.facebook.com/groups/foringerdol/</span
                        >
                      </a>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="smalldiv">
            <div v-for="event in events" :key="event.id">
              <div class="product clearfix" v-if="this.id == event.id">
                <div class="smallevent">
                  <div class="product-image">
                    <a href=""
                      ><img
                        style="width: 270px; height: 220px"
                        :src="event.img1"
                        alt=""
                    /></a>
                    <a href=""
                      ><img
                        style="width: 270px; height: 220px"
                        :src="event.img2"
                        alt=""
                    /></a>
                  </div>
                  <div id="text">
                    <div class="product-title">
                      <h4 class="pt-3">
                        {{ event.name }}
                      </h4>
                      <h3>৳ {{ event.price }}</h3>
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
                    <h3>Upcomming Events</h3>
                    <div class="tab-content clearfix" id="tabs-1">
                      <div id="popular-post-list-sidebar">
                        <div
                          class="spost clearfix"
                          v-for="event in events.slice(0, 6)"
                          :key="event"
                        >
                          <router-link
                            :to="{
                              name: 'EventDetails',
                              params: { id: event.id },
                            }"
                          >
                            <div class="entry-image">
                              <a href="#" class="nobg"
                                ><img :src="event.img1" alt=""
                              /></a>
                            </div>
                            <div class="entry-title">
                              <h4>
                                {{ event.name }}
                              </h4>
                            </div>
                          </router-link>
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
                    <a href="#activities">Activities</a>
                    <a href="#inclusions">Inclusions</a>
                    <a href="#exclusions">Exclusions</a>
                    <a href="#instructions">Policy</a>
                    <a href="#price">Price</a>
                    <a href="#fb_group">Facebook Group</a>
                    <a href="#events">Events</a>
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
import { VueperSlide, VueperSlides } from "vueperslides";
import "vueperslides/dist/vueperslides.css";
import { mapState } from "vuex";
import Footer from "../components/Footer1";
import Navbar from "../components/Navbar";

export default {
  data() {
    return {
      book: false,
      picked: "",
    };
  },
  methods: {
    booknow() {
      this.book = true;
    },
    toCheckout(event) {
      this.$router.push({
        name: "Checkout",
        query: {
          type: "events",
          p: this.picked.price,
          pack: this.picked.package,
        },
      });
      this.$store.dispatch("productbox/addevent", event);
      console.log(event);
      console.log(this.picked.price);
    },
  },
  props: ["id"],
  computed: {
    ...mapState("productbox", ["events"]),
  },

  components: {
    Navbar,
    Footer,
    VueperSlides,
    VueperSlide,
  },
};
</script>

<style scoped>
html {
  scroll-behavior: smooth;
  height: 100%;
  width: 100%;
  margin: 0;
}
.evntDetails {
  display: flex;
}

.vueperslides--fixed-height {
  height: 500px;
  width: 800px;
}

.container {
  display: flex;
}
.entry-title {
  margin-top: 5%;
}
.content-wrap {
  padding: 0;
}
.smallevent {
  padding-bottom: 10%;
  background-color: rgb(250, 250, 242);
}
.entry-title h4 {
  text-align: center;
}
.product-title h3 {
  margin-top: -10%;
}
.entry {
  margin: 0;
  padding: 0;
}
#booknow {
  color: #ffffff;
}
.entry-content p {
  margin: 0;
}
.price-color {
  background-color: #fafaf2;
  padding: 1% 3%;
}
.entry-content h4 {
  margin: 0;
}
/* .price-details {
  width: 100px;
} */

#price-D {
  width: 100px;
}
#price-D div {
  padding: 5% 20%;
}
/* #price {
  background-color: #fafaf2;
} */

.package-heading .head1 {
  position: relative;
  left: -30%;
}
.package-heading .head2 {
  position: relative;
  right: -50%;
}
#totalprice-smallevent {
  display: flex;
  background-color: #fafaf2;
  margin-bottom: 5%;
}
.smallevent-details p,
#map-icon {
  margin: 0;
  font-size: 1.5rem;
}
.smallevent-details {
  padding-top: 2%;
  padding-left: 3%;
}
.booking {
  width: 600px;
}
.hotel div {
  padding: 0% 1% 0% 0%;
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
  margin-right: -1%;
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
#btn:hover {
  color: #42b983;
}
#social .btnP {
  background-color: #cb2027;
}
#social a {
  padding: 2% 15%;
  font-size: 2.5rem;
  color: #fff;
}
.description p {
  padding-bottom: 5%;
}

.entry-content i {
  font-size: 0.9rem;
  padding-right: 1%;
}
#sidebar-tabs {
  margin-bottom: 20%;
}
#sidebar-tabs h3 {
  margin-top: 20%;
  margin-bottom: 10%;
}
#content {
  margin-top: 2%;
  margin-bottom: 2%;
}
#tags {
  padding-top: 7%;
}
</style>
