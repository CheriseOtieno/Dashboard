<template>
    <div :class="['side-bar', { open: isOpen }]">
        <h3 class="sideheading">AMS</h3>
        <ul>
            <li><router-link to="/about" @click="closeSidebar">🧾 About</router-link></li>
            <li><router-link to="/costs" @click="closeSidebar">💰 Costs</router-link></li>
            <li><router-link to="/offices" @click="closeSidebar">🏢 Offices</router-link></li>
            <li><router-link to="/employees" @click="closeSidebar">👥 Employees</router-link></li>
            <li><router-link to="/categories" @click="closeSidebar">🗂️ Categories</router-link></li>
            <li><router-link to="/contactinfo" @click="closeSidebar">📞 Contact Information</router-link></li>
        </ul>
    </div>
</template>
  
<script>
    export default {
        props: {
            isOpen: Boolean
        },
        methods: {
            closeSidebar() {
                this.$emit('toggleSidebar'); 
            }
        }
    }
</script>
  
<style scoped>
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
  
    .side-bar ul {
        list-style: none;
        padding-left: 0;
    }
  
    .side-bar li {
        padding: 10px;
        text-align: left;
        font-size: 16px;
    }
  
    .side-bar li a,
    .side-bar li router-link {
        text-decoration: none;
        color: inherit;
        transition: color 0.3s ease, transform 0.2s ease;
    }
  
    .side-bar li a:hover,
    .side-bar li router-link:hover {
        background-color: #ff4d6d;
        transform: scale(1.05);
        border-radius: 5px;
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
    }
</style>
  