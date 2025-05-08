<template id = "offices">
    <main class="officespage">
        <section class="card">
            <h3 id="offices">OFFICES</h3>
        </section>
        <p>To ensure broad national coverage, Afya Medical Services maintains regional distribution centers and satellite offices across Kenya. These offices are strategically placed to optimize delivery efficiency and minimize response times. Our current office locations include:

Nairobi – Main headquarters and national operations center.

Mombasa – Coastal logistics and sea import handling.

Kisumu – Western region supply and support hub.

Eldoret – North Rift distribution center and regional warehouse.

Nakuru – Central Rift logistics center with pharmacy partnerships.

Nyeri – Mt. Kenya region distribution and outpatient service coordination.

Kakamega – Western health support and outreach coordination.

Machakos – Lower Eastern delivery and inventory point.

Each office is equipped with storage facilities, delivery vehicles, and trained personnel to handle medical goods with care. Plans are underway to expand into Garissa, Kitale, and Meru in the near future.</p>

        <div class="offices-section">
            <img
            src="/home/vallary/Pictures/Screenshots/Screenshot from 2025-05-05 13-27-00.png"
            alt="Offices"
            class="office-img"
            />
            <div class="table-container">
                <table>
                    <thead>
                        <tr>
                            <th>County</th>
                            <th>Office Location</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="(office, index) in offices" :key="index">
                            <td>{{ office.county }}</td>
                            <td>{{ office.location }}</td>
                        </tr>
                    </tbody>
                </table>
                <button @click="editMode = !editMode">
                    {{ editMode ? "Finish Editing" : "Edit Table" }}
                </button>

                <div v-if="editMode">
                    <h4>Add New Office</h4>
                    <input v-model="newCounty" placeholder="County" />
                    <input v-model="newLocation" placeholder="Office Location" />
                    <button @click="addOffice">Add</button>

                    <h4>Delete Office (Index)</h4>
                    <input type="number" v-model.number="deleteIndex" />
                    <button @click="deleteOffice">Delete</button>
                </div>
            </div>
        </div>
    </main>
</template>

<style scoped>

    .officespage {
        background: linear-gradient(45deg, #f8c9d4, #ffd6e3); 
        color: #333;
        padding: 2rem;
        font-family: 'Roboto', sans-serif;
    }
  
  
    .officespage p {
        font-size: 16px;
        line-height: 1.6;
    }

    .card {
        background-color: black;
        border-radius: 4px;
        padding: 1.5rem;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        margin-bottom: 2rem;
    }

    .officespage h3 {
        color: pink;
        font-family:Verdana, Geneva, Tahoma, sans-serif;
    }

    .offices-section {
        display: flex;
        gap: 2rem;
        margin: 2rem 0;
        flex-wrap: wrap;
    }

    .office-img {
        max-width: 400px;
        border-radius: 8px;
    }

    .table-container {
        flex: 1;
        min-width: 300px;
    }

    table {
        width: 100%;
        border-collapse: collapse;
        margin-bottom: 1rem;
    }

    th,
    td {
        border: 1px solid #ccc;
        padding: 0.5rem;
        text-align: left;
    }

    button {
        margin-top: 0.5rem;
    }


</style>

<script>
    export default {
        data() {
            return {
                showModal: false,
                editMode: false,
                offices: [
                    { county: 'Nairobi', location: 'Main HQ' },
                    { county: 'Mombasa', location: 'Coastal Hub' },
                ],
                newCounty: '',
                newLocation: '',
                deleteIndex: null
            };
        },
        methods: {
            submitForm() {
                alert("Form submitted!");
                this.showModal = false;
            },
            addOffice() {
                if (this.newCounty && this.newLocation) {
                    this.offices.push({
                        county: this.newCounty,
                        location: this.newLocation
                    });
                    this.newCounty = '';
                    this.newLocation = '';
                }
            },
            deleteOffice() {
                if (
                    this.deleteIndex !== null &&
                    this.deleteIndex >= 0 &&
                    this.deleteIndex < this.offices.length
                ) {
                    this.offices.splice(this.deleteIndex, 1);
                    this.deleteIndex = null;
                } else {
                    alert("Invalid index!");
                }
            }

        }

    }
</script>