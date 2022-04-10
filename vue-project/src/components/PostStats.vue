<template>
  <!-- Metrics Data Blocks -->
  <div class="metrics-container">
    <div class="metrics-block" :class="{ inactive: !statsImpressions }">
      <span>{{ statsImpressions }}</span>
      <label>Impressions</label>
    </div>

    <div class="metrics-block" :class="{ inactive: !statsReach }">
      <span>{{ statsReach }}</span>
      <label>Reach</label>
    </div>
    <div class="metrics-block" :class="{ inactive: !statsEngagement }">
      <span class="percentage">{{ statsEngagement }}</span>
      <label>Engagement</label>
    </div>
  </div>
</template>

<script>
export default {
  props: ["statsImpressions", "statsReach", "statsEngagement"],
};
</script>

<style>
/* Metrics/Stats Blocks Styling */
.metrics-container {
  display: flex;
  justify-content: space-between;
  width: 100%;
}

.metrics-block {
  background-color: var(--cq-c-white-005);
  border-radius: var(--cq-default-border-radius);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: var(--cq-c-white);
  height: 4.3rem;
  padding: 0.8rem;
  transition: var(--cq-transition-out);
  width: 32%;
}

.metrics-block span {
  color: var(--cq-c-grey-lightest);
  font-size: 1.1rem;
}

.metrics-block span.percentage::after {
  content: "%";
}

.metrics-block label {
  color: var(--cq-c-grey-medium);
  font-size: 0.7rem;
  text-transform: uppercase;
}

/* Empty Metrics/Stats Block Styling */
.metrics-block.inactive {
  opacity: 0.35;
}
.metrics-block.inactive span::after {
  content: "-";
  text-align: center;
}
</style>
