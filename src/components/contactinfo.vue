<template id="contactinfo">
    <main class="contactinfopage">
        <div>
            <button class="createaccount" @click="showModal = true">CREATE AN ACCOUNT?</button>
        </div>

        <div v-if="showModal" class="modal-overlay" @click.self="showModal = false">
            <div class="modal-content">
                <h3>Create an Account</h3>
                <form @submit.prevent="submitForm">
                    <input type="text" placeholder="Full Name" required />
                    <input type="email" placeholder="Email" required />
                    <input type="password" placeholder="Password" required />
                    <button type="submit">Submit</button>
                </form>
                <button @click="showModal = false">Close</button>
            </div>
        </div>

        <section class="card">
            <h3 id="contactinfo">CONTACT INFORMATION</h3>
        </section>
        <p>Afya Medical Services values open and accessible communication. Whether you're a hospital seeking a new supplier, a clinic needing emergency stock, or a patient with a prescription to be filled, we’re here to help.</p>

        <p>Phone Number: +254 712 345 678</p>
        <p class="email"> cheriseotieno1707@gmail.com</p>

        <p>You can also visit any of our regional offices or contact us via our official social media pages. We are working toward launching an online portal and mobile app to allow real-time tracking, ordering, and support.

We look forward to being your trusted partner in healthcare delivery.</p>
    </main>
</template>

<style scoped>

    .contactinfopage {
        background: linear-gradient(45deg, #f8c9d4, #ffd6e3); 
        color: #333;
        padding: 2rem;
        font-family: 'Roboto', sans-serif;
    }
  
  
    .contactinfopage p {
        font-size: 16px;
        line-height: 1.6;
    }

    .email {
        color: blue;
    }

    .card {
        background-color: black;
        border-radius: 4px;
        padding: 1.5rem;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        margin-bottom: 2rem;
    }

    .contactinfopage h3 {
        color: pink;
        font-family:Verdana, Geneva, Tahoma, sans-serif;
    }

    .createaccount {
        padding: 3.5px;
        margin-bottom: 2rem;
        margin-top: 2rem;
        cursor: pointer;
        animation: heartbeat 1.5s infinite;
        transition: transform 0.2s ease-in-out;
    }

    @keyframes heartbeat {
        0% {
            transform: scale(1);
        }
        14% {
            transform: scale(1.3);
        }
        28% {
            transform: scale(1);
        }
        42% {
            transform: scale(1.3);
        }
        70% {
            transform: scale(1);
        }
    }

    .modal-overlay {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0,0,0,0.5);
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 1000;
    }

    .modal-content {
        background: white;
        padding: 2rem;
        border-radius: 8px;
        width: 90%;
        max-width: 400px;
        box-shadow: 0 4px 10px rgba(0,0,0,0.3);
    }


</style>

<script>
    export default {
        name: 'contactinfo',
        data() {
            return {
                showModal: false
            }
        },
        methods: {
            submitForm() {
                alert('Account created successfully!');
                this.showModal = false;
            }
        }
    }
</script>
