<template>
  <div class="cards-container">
    <post-details-card
      v-for="post in postDetail"
      :key="post"
      :images="post.images"
      :influencerName="post.influencerName"
      :influencerImage="post.influencerImage"
      :handle="post.handle"
      :postingDate="post.postingDate"
      :statsImpressions="post.stats.impressions"
      :statsReach="post.stats.reach"
      :statsEngagement="post.stats.engagement"
      :statslabel="post.stats.index"
    ></post-details-card>
  </div>
</template>

<script>
import PostDetailsCard from "./components/PostDetailsCard.vue";
import sampleData from "./mock-data/sample-data.json";

export default {
  data() {
    return {
      postDetail: sampleData,
    };
  },
  components: {
    PostDetailsCard,
  },
};
</script>

<style>
@import "./assets/main.css";

#app {
  background-color: var(--cq-c-grey-dark);
  height: 100%;
  min-height: 100vh;
  width: 100%;
  padding: 4rem;
}

.cards-container {
  display: flex;
  flex-flow: row wrap;
  justify-content: center;
  align-items: flex-start;
  gap: 50px;
  max-width: 1600px;
  min-width: 750px;
  margin: 0 auto;
}
</style>
