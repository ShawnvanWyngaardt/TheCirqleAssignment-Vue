<template>
  <!-- Influencer Details Section -->
  <div class="post-profile-data-container">
    <div class="post-profile-data">
      <img
        class="post-profile-img"
        :src="influencerImage"
        :alt="influencerName"
      />
      <div class="post-profile-details">
        <span class="name">{{ influencerName }}</span>
        <span class="handle">
          {{ handle }} <i class="fa-solid fa-angle-right"></i>
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["influencerName", "influencerImage", "handle"],
};
</script>

<style>
/* Influencer Section Styling */
.post-profile-data-container {
  background: linear-gradient(rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.9) 90%);
  border-bottom-left-radius: var(--cq-default-border-radius);
  border-bottom-right-radius: var(--cq-default-border-radius);
  display: flex;
  align-items: flex-end;
  height: 40%;
  position: absolute;
  padding: 1rem;
  bottom: 0;
  left: 0;
  width: 100%;
  z-index: 3;
}

.post-profile-data {
  display: flex;
  gap: 15px;
}

.post-profile-data:hover {
  cursor: pointer;
}

.post-profile-img {
  background-color: var(--cq-c-grey-lightest);
  border-radius: 50%;
  border: 2px solid var(--cq-c-grey-lightest);
  height: 50px;
  transition: var(--cq-transition-out);
  width: 50px;
}

.post-profile-details {
  display: flex;
  font-size: 16px;
  flex-direction: column;
  height: 50px;
  justify-content: space-between;
  padding: 0;
}

.post-profile-details .name {
  color: var(--cq-c-white);
  font-weight: 900;
  transition: var(--cq-transition-out);
}

.post-profile-details .handle {
  color: var(--cq-c-grey-medium);
  font-weight: 400;
  position: relative;
  transition: var(--cq-transition-out);
}

.post-profile-details .handle .fa-angle-right {
  color: var(--cq-c-grey-lightest);
  font-size: 0.8rem;
  opacity: 0;
  transform: translateX(-2px);
  transition: var(--cq-transition-out);
}

.post-profile-data:hover .name {
  color: var(--cq-c-accent);
  transition: var(--cq-transition-in);
}

.post-profile-data:hover .handle {
  color: var(--cq-c-white);
  transition: var(--cq-transition-in);
}

.post-profile-data:hover .handle .fa-angle-right {
  color: var(--cq-c-accent);
  opacity: 1;
  transform: translateX(8px);
  transition: var(--cq-transition-in);
}
</style>
