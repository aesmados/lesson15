<template>
  <div class="overlay">
    <div class="more-modal">
      <button class="btn btn-danger" @click="closeModal">&#x2715;</button>
      <slot></slot>
    </div>
  </div>
</template>
<script>
export default {
  methods: {
    closeModal() {
      this.$emit("close-modal");
    },
  },
};
</script>
<style scoped>
.btn-danger {
  position: absolute;
  top: -20px;
  right: -20px;
  width: 40px;
  height: 40px;
  text-align: center;
}
.overlay {
  position: fixed;
  z-index: 99;
  background: rgba(0, 0, 0, 0.3);
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  overflow: hidden;
  height: 100vh;
}
.more-modal {
  position: relative;
  top: 20%;
  width: 50%;
  min-height: 30vh;
  margin: auto;
  background: #fff;
  padding: 20px;
  text-align: center;
}
</style>
