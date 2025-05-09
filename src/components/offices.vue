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
        width:100%;
        border-radius: 8px;
    }

</style>

<script>
    export default {
        name: 'offices'
    }
</script>
