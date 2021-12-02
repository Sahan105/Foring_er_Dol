<template>
    <div class="slider"> 
      <vueper-slides :fixed-height="true" :bullets="true" fade autoplay>
      <vueper-slide
        v-for="slide in slides"
        :key="slide"
        :image="slide.image" 
      />
    </vueper-slides>
    </div>
</template>

<script>
import { mapState } from "vuex";
import { VueperSlides, VueperSlide } from "vueperslides";
import "vueperslides/dist/vueperslides.css";
export default {
  name: "slider",
  computed: {
    ...mapState("slider", ["slides"]),
  },
  components: { VueperSlides, VueperSlide },
};
</script>
<style scoped>
.carousel__slide {
  height: 70vh;
}

.carousel__prev,
.carousel__next {
  box-sizing: border-box;
  border: 40px solid white;
}
.vueperslides__arrow {
  display: none;
}
</style>
