<template>
  <main class="categoriespage">
    <section class="card">
      <h3>CATEGORIES</h3>
    </section>

    <div class="category-holder">
      <div class="prescription" @click="showForm = true">
        <h4>PRESCRIPTION</h4>
        <p>Do you need a drug to be prescribed to you?</p>
      </div>

      <div class="consultation" @click="showConsultationForm = true">
        <h4>CONSULTATION</h4>
        <p>Need to consult a doctor?</p>
      </div>

      <div class="supply" @click="showSupplyForm = true">
        <h4>SUPPLY</h4>
        <p>Are you an organization that needs medicine supply?</p>
      </div>

      <div class="delivery" @click="showDeliveryForm = true">
        <h4>DELIVERY</h4>
        <p>Do you need a delivery to your location?</p>
      </div>
    </div>

    <div v-if="showForm" class="modal-overlay">
      <div class="modal-content">
        <h3>Prescription Form</h3>
        <form @submit.prevent="submitForm('Prescription')">
          <label>Name: <input type="text" v-model="form.name" required /></label>
          <label>Age: <input type="number" v-model="form.age" required /></label>
          <label>Weight (kg): <input type="number" v-model="form.weight" required /></label>
          <label>Height (cm): <input type="number" v-model="form.height" required /></label>
          <label>Issue: <input type="text" v-model="form.issue" required /></label>
          <label>Email: <input type="email" v-model="form.email" required /></label>
          <div class="form-buttons">
            <button type="submit">Submit</button>
            <button type="button" @click="cancelForm('Prescription')">Cancel</button>
          </div>
        </form>
      </div>
    </div>

    <div v-if="showConsultationForm" class="modal-overlay">
      <div class="modal-content">
        <h3>Consultation Form</h3>
        <form @submit.prevent="submitConsultationForm">
          <label>Name: <input type="text" v-model="consultationForm.name" required /></label>
          <label>ID number: <input type="text" v-model="consultationForm.id" required /></label>
          <label>Phone number: <input type="text" v-model="consultationForm.phone" required /></label>
          <label>Email: <input type="email" v-model="consultationForm.email" required /></label>
          <div class="form-buttons">
            <button type="submit">Submit</button>
            <button type="button" @click="cancelForm('Consultation')">Cancel</button>
          </div>
        </form>
      </div>
    </div>

    <div v-if="showSupplyForm" class="modal-overlay">
      <div class="modal-content">
        <h3>Supply Form</h3>
        <form @submit.prevent="submitSupplyForm">
          <label>Organization name: <input type="text" v-model="supplyForm.name" required /></label>
          <label>Contact Info: <input type="text" v-model="supplyForm.contactinfo" required /></label>
          <label>Email: <input type="email" v-model="supplyForm.email" required /></label>
          <div class="form-buttons">
            <button type="submit">Submit</button>
            <button type="button" @click="cancelForm('Supply')">Cancel</button>
          </div>
        </form>
      </div>
    </div>

    <div v-if="showDeliveryForm" class="modal-overlay">
      <div class="modal-content">
        <h3>Delivery Form</h3>
        <form @submit.prevent="submitDeliveryForm">
          <label>Name: <input type="text" v-model="deliveryForm.name" required /></label>
          <label>Phone Number: <input type="text" v-model="deliveryForm.phonenumber" required /></label>
          <label>Email: <input type="email" v-model="deliveryForm.email" required /></label>
          <label>Address: <input type="text" v-model="deliveryForm.address" required /></label>
          <div class="form-buttons">
            <button type="submit">Submit</button>
            <button type="button" @click="cancelForm('Delivery')">Cancel</button>
          </div>
        </form>
      </div>
    </div>

    <activitytable :activityData="activityLog" />
  </main>
</template>

<script>
import activitytable from './activitytable.vue';

export default {
  name: 'categories',
  components: {
    activitytable
  },
  data() {
    return {
      showForm: false,
      showConsultationForm: false,
      showSupplyForm: false,
      showDeliveryForm: false,
      activityLog: [],
      form: { name: '', age: '', weight: '', height: '', issue: '', email: '' },
      consultationForm: { name: '', id: '', phone: '', email: '' },
      supplyForm: { name: '', contactinfo: '', email: '' },
      deliveryForm: { name: '', phonenumber: '', email: '', address: '' }
    };
  },
  created() {
    const storedLog = localStorage.getItem('activityLog');
    if (storedLog) {
      this.activityLog = JSON.parse(storedLog);
    }
  },
  methods: {
    logActivity(category, success) {
      const date = new Date().toLocaleString();
      const newEntry = { category, date, success };
      this.activityLog.push(newEntry);
      localStorage.setItem('activityLog', JSON.stringify(this.activityLog));
    },
    submitForm(category) {
      this.logActivity(category, true);
      this.showForm = false;
    },
    submitConsultationForm() {
      this.logActivity('Consultation', true);
      this.showConsultationForm = false;
    },
    submitSupplyForm() {
      this.logActivity('Supply', true);
      this.showSupplyForm = false;
    },
    submitDeliveryForm() {
      this.logActivity('Delivery', true);
      this.showDeliveryForm = false;
    },
    cancelForm(category) {
      this.logActivity(category, false);
      this.showForm = this.showConsultationForm = this.showSupplyForm = this.showDeliveryForm = false;
    }
  }
};
</script>

<style scoped>
.categoriespage {
  background: linear-gradient(45deg, #f8c9d4, #ffd6e3);
  padding: 2rem;
  font-family: 'Roboto', sans-serif;
}

.card {
  background-color: black;
  padding: 1rem;
  margin-bottom: 2rem;
  border-radius: 6px;
}

.card h3 {
  color: pink;
  margin: 0;
  text-align: center;
}

.category-holder {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 1rem;
  justify-content: center;
}

.category-holder > div {
  background-color: lightblue;
  border: 1px solid #ccc;
  border-radius: 12px;
  padding: 1rem;
  text-align: center;
  cursor: pointer;
  transition: transform 0.2s;
}

.category-holder > div:hover {
  transform: scale(1.05);
}

@media (max-width: 768px) {
  .category-holder {
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
  }

  .category-holder > div {
    margin-bottom: 1rem;
  }
}

.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.4);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal-content {
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
  width: 90%;
  max-width: 400px;
}

.modal-content label {
  display: block;
  margin-bottom: 0.75rem;
}

.modal-content input {
  width: 100%;
  padding: 0.5rem;
  margin-top: 0.3rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.form-buttons {
  display: flex;
  justify-content: space-between;
  margin-top: 1rem;
}

.form-buttons button {
  padding: 0.5rem 1rem;
  background-color: #f8c9d4;
  border: none;
  border-radius: 6px;
  font-weight: bold;
  cursor: pointer;
}

.form-buttons button:hover {
  background-color: #ffb6c1;
}
</style>
