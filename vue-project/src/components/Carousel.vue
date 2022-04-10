<template>
  <div class="carousel">
    <slot></slot>
  </div>
</template>

<script>
export default {
  methods: {
    next() {
      this.$emit("next");
    },
    prev() {
      this.$emit("prev");
    },
  },
};
</script>

<style>
.carousel-btn {
  background-color: var(--cq-c-white-005);
  border: none;
  border-radius: 50%;
  color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 25px;
  width: 25px;
  transition: var(--cq-transition-out);
}
.carousel-btn:hover {
  background-color: var(--cq-c-accent);
  cursor: pointer;
  transition: var(--cq-transition-in);
}
</style>
