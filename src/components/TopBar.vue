<template>
  <header class="top-bar">
    <div class="hamburger" @click="toggleSidebar">
      &#9776; 
    </div>
    <div class="title">AMS</div>
  </header>
</template>

<script>
export default {
  methods: {
    toggleSidebar() {
      this.$emit('toggleSidebar'); 
    }
  }
}
</script>

<style scoped>
  .top-bar {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    background-color: #333;
    color: white;
    padding: 0.5rem;
    font-size: 1.8rem;
    font-weight: bold;
    z-index: 1000;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .hamburger {
    font-size: 2rem;
    cursor: pointer;
  }

  .title {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    font-size: 2rem;
  }
</style>
