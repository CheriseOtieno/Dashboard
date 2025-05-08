<template>
  <div class="dashboard">
    <TopBar @toggleSidebar="toggleSidebar" />
    <div class="content">
      <SideBar :isOpen="isSidebarOpen" @toggleSidebar="toggleSidebar" />
      <div class="main-page" :class="{'shifted': isSidebarOpen}">
        <router-view />
      </div>
    </div>
  </div>
</template>

<script>
  import TopBar from './components/TopBar.vue'
  import SideBar from './components/SideBar.vue'

  export default {
    components: {
      TopBar,
      SideBar
    },
    data() {
      return {
        isSidebarOpen: false
      }
    },
    methods: {
      toggleSidebar() {
        this.isSidebarOpen = !this.isSidebarOpen;
      }
    }
  }
</script>

<style scoped>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box; 
  }

  .dashboard {
    display: flex;
    flex-direction: column;
    height: 100vh;
    overflow-x: hidden; 
  }

  .content {
    display: flex;
    flex: 1;
    margin-top: 60px; 
  }

  .side-bar {
    width: 250px;
    position: fixed;
    top: 0;
    left: 0;
    bottom: 0;
    background-color: #222;
    color: white;
    padding-top: 20px;
    transition: transform 0.3s ease;
    z-index: 100;
  }

  .main-page {
    flex: 1;
    padding: 20px;
    transition: margin-left 0.3s ease;
    margin-left: 250px;
    overflow-x: hidden; 
    word-wrap: break-word; 
    width: 100%;
    box-sizing: border-box;
  }

  .main-page.shifted {
    margin-left: 250px;
  }

  @media (max-width: 1024px) {
    .side-bar {
      transform: translateX(-100%);
      width: 80%;
      position: absolute;
      top: 0;
      left: 0;
      height: 100vh;
      z-index: 1000;
    }

    .side-bar.open {
      transform: translateX(0);
    }

    .side-bar ul {
      padding: 0;
    }

    .side-bar li {
      text-align: center;
      padding: 15px;
    }

    .sideheading {
      text-align: center;
      padding: 10px;
    }

    .main-page {
      margin-left: 0;
      padding: 10px;
      overflow-x: hidden; 
      width: 100%; 
    }

    .main-page.shifted {
      margin-left: 80%;
    }
  }
</style>
