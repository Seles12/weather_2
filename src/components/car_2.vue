<template>
  <div>
    <div class="car_2">
      <b-carousel
        id="carousel-1"
        v-model="slide"
        :interval="4000"
        controls
        indicators
        background="#ababab"
        img-width="1024"
        img-height="480"
        style="text-shadow: 1px 1px 2px #333"
        @sliding-start="onSlideStart"
        @sliding-end="onSlideEnd"
      >
        <!-- Text slides with image -->
        <b-carousel-slide>
          <template #img>
            <img
              class="d-block img-fluid w-100"
              width="1024"
              height="480"
              src="https://picsum.photos/1024/480/?image=193"
              alt="image slot"
            />
          </template>
        </b-carousel-slide>

        <!-- Slides with custom text -->
        <b-carousel-slide
          img-src="https://picsum.photos/1024/480/?image=197"
        ></b-carousel-slide>
        <b-carousel-slide
          img-src="https://picsum.photos/1024/480/?image=84"
        ></b-carousel-slide>
        <b-carousel-slide
          img-src="https://picsum.photos/1024/480/?image=110"
        ></b-carousel-slide>
        <b-carousel-slide
          img-src="https://picsum.photos/1024/480/?image=187"
        ></b-carousel-slide>
        <b-carousel-slide
          img-src="https://picsum.photos/1024/480/?image=164"
        ></b-carousel-slide>
        <b-carousel-slide
          img-src="https://picsum.photos/1024/480/?image=206"
        ></b-carousel-slide>

        <!-- Slides with image only -->
        <b-carousel-slide img-src="https://picsum.photos/1024/480/?image=238" />

        <!-- Slides with img slot -->
        <!-- Note the classes .d-block and .img-fluid to prevent browser default image alignment -->
        <b-carousel-slide>
          <template #img>
            <img
              class="d-block img-fluid w-100"
              width="1024"
              height="480"
              src="https://picsum.photos/1024/480/?image=255"
              alt="image slot"
            />
          </template>
        </b-carousel-slide>
      </b-carousel>

      <weather_2 id="weather-widget" />
    </div>
  </div>
</template>
<script>
import weather_2 from "./weather_2.vue";
export default {
  components: { weather_2 },
  data() {
    return {
      slide: 0,
      sliding: null,
    };
  },
  methods: {
    onSlideStart(slide) {
      this.sliding = true;
    },
    onSlideEnd(slide) {
      this.sliding = false;
    },
  },
};
</script>

<style scoped>
#weather-widget {
  position: absolute;
  top: 25%;
  left: 50%;
  transform: translate(-50%, -25%);
}
.car_2 {
  width: auto;
  height: auto;
}
</style>
