<template>
  <div class="card">
    <!-- Top Content Section of the Card -->
    <div class="card-top">
      <!-- Carousel / Image Block -->
      <div class="carousel-container">
        <Carousel @next="next" @prev="prev">
          <CarouselSlide
            v-for="(image, index) in images"
            :key="image"
            :index="index"
            :visibleSlide="visibleSlide"
            :direction="direction"
            class="img-block"
          >
            <img :src="image" class="card-top-blur-bg" />
            <img
              :src="image"
              class="top-img"
              :alt="'image by' + ' ' + influencerName"
            />
          </CarouselSlide>
        </Carousel>
        <PostProfile
          :influencerName="influencerName"
          :influencerImage="influencerImage"
          :handle="handle"
        ></PostProfile>
        <!-- Carousel / Controls -->
        <div class="carousel-controls" :class="{ inactive: slidesLength <= 1 }">
          <button @click="prev" class="carousel-btn">
            <i class="fa-solid fa-angle-left"></i>
          </button>
          <button @click="next" class="carousel-btn">
            <i class="fa-solid fa-angle-right"></i>
          </button>
        </div>
      </div>
    </div>

    <!-- Posted Date -->
    <div class="date">
      Posted on
      <strong>{{ moment(postingDate).format("MMMM Do YYYY") }}</strong>
    </div>
    <PostStats
      :statsImpressions="statsImpressions"
      :statsReach="statsReach"
      :statsEngagement="statsEngagement"
    ></PostStats>
  </div>
</template>

<script>
import moment from "moment";
import Carousel from "./Carousel.vue";
import CarouselSlide from "./CarouselSlide.vue";
import PostProfile from "./PostProfile.vue";
import PostStats from "./PostStats.vue";

export default {
  components: {
    Carousel: Carousel,
    CarouselSlide: CarouselSlide,
    PostProfile: PostProfile,
    PostStats: PostStats,
  },
  props: [
    "images",
    "postingDate",
    "influencerName",
    "influencerImage",
    "handle",
    "statsImpressions",
    "statsReach",
    "statsEngagement",
  ],
  data() {
    return {
      visibleSlide: 0,
      direction: "left",
    };
  },
  computed: {
    slidesLength() {
      return this.images.length;
    },
  },
  methods: {
    // Converts DATE to be easily readable
    moment(postingDate) {
      return moment(postingDate);
    },
    // Carousel Controls
    next() {
      if (this.visibleSlide >= this.slidesLength - 1) {
        this.visibleSlide = 0;
      } else {
        this.visibleSlide++;
      }
      this.direction = "left";
    },
    prev() {
      if (this.visibleSlide <= 0) {
        this.visibleSlide = this.slidesLength - 1;
      } else {
        this.visibleSlide--;
      }
      this.direction = "right";
    },
  },
};
</script>

<style>
/* Main Card Styling */
.card {
  display: flex;
  flex-flow: column;
  justify-content: space-between;
  height: var(--cq-card-dimension-h);
  margin-bottom: 10px;
  width: var(--cq-card-dimension-w);
}

.card-top {
  height: 474px;
  position: relative;
  width: 100%;
}

.card-top:hover .post-profile-img {
  border-color: var(--cq-c-accent);
}
.card:hover .metrics-block {
  background-color: var(--cq-c-purple-017);
  transition: var(--cq-transition-in);
}

/* Carousel */
.carousel-container {
  height: 100%;
  position: relative;
}
.carousel {
  height: var(--cq-card-dimension-w);
  overflow: hidden;
  position: relative;
  width: var(--cq-card-dimension-w);
  z-index: 2;
}
/* >>> If for whatever reason the carousel slide is empty */
.carousel:empty {
  border-radius: var(--cq-default-border-radius);
  height: 100%;
  background: url(../assets/img/fallback.png);
}

.carousel:empty + .carousel-controls {
  display: none;
}

/* Carousel Images */
.img-block {
  border-radius: var(--cq-default-border-radius);
  display: flex;
  height: 100%;
  overflow: hidden;
  position: absolute;
  width: 100%;
}

.card-top-blur-bg {
  background: var(--cq-c-grey-darkest);
  background-size: cover;
  display: block;
  filter: blur(12px);
  -webkit-filter: blur(12px);
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
}

.top-img {
  background: var(--cq-image-loading-bg);
  height: 100%;
  margin: 0 auto;
  max-width: 100%;
  position: relative;
  width: auto;
}

.carousel-controls {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 30px;
  margin: 0 auto;
  position: absolute;
  top: 50%;
  left: 0;
  right: 0;
  width: 98%;
  z-index: 4;
}
.carousel-controls.inactive {
  display: none;
}

/* Posting Date Styling */
.date {
  color: var(--cq-c-grey-medium);
  font-size: 0.75rem;
  padding-top: 7px;
  text-align: center;
}

.date > strong {
  color: var(--cq-c-grey-lightest);
  font-weight: 700;
}
</style>
