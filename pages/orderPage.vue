<template>
  <section class="order-page">
    
        <!-- HEADER -->
        <div class="order-header container">
          <h1>Place Your Order</h1>
          <p>
            Place your order in just a few easy steps, delivering freshly prepared
            dishes with consistent quality and on-time service.
          </p>
        </div>

    <div class="container order-layout">

      <!-- LEFT + CENTER -->
      <div class="menu-area">

        <!-- SEARCH + FILTER -->
        <div class="menu-actions">
          <input type="text" placeholder="Search Category or Menu" />
          <button class="filter-btn">Filter</button>
        </div>

        <!-- CATEGORY SLIDER -->
        <div class="category-slider">
          <button class="slide-btn" @click="scrollCats(-1)">‹</button>
          <div class="category-track" ref="catTrack">
            <span v-for="cat in categories" :key="cat">{{ cat }}</span>
          </div>
          <button class="slide-btn" @click="scrollCats(1)">›</button>
        </div>

        <!-- FOOD GRID -->
        <div class="food-grid">
          <div v-for="item in items" :key="item.id" class="food-card">
            <img src="/images/biryani.jpg" alt="food" />

            <div class="food-info">
              <h3>{{ item.name }}</h3>
              <p>{{ item.desc }}</p>

              <div class="food-bottom">
                <span class="price">₹{{ item.price }}</span>
                <button>Add</button>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- RIGHT SUMMARY -->
      <aside class="order-summary">
        <h3>Order Summary</h3>
        <p class="summary-note">
          A clear overview of your order with complete transparency on items,
          pricing and totals.
        </p>

        <div class="summary-list">
          <div v-for="item in items.slice(0, 6)" :key="item.id" class="summary-item">
            <img src="/images/biryani.jpg" />
            <div>
              <h4>{{ item.name }}</h4>
              <span>₹{{ item.price }}</span>
            </div>
          </div>
        </div>

        <button class="confirm-btn">Confirm Order</button>
      </aside>

    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";

const catTrack = ref(null);

const scrollCats = (dir) => {
  catTrack.value.scrollBy({ left: dir * 120, behavior: "smooth" });
};

const categories = [
  "Biryani",
  "Appetizers",
  "Drinks",
  "Noodles",
  "Salad",
  "Desserts",
  "Combos",
];

const items = Array.from({ length: 12 }, (_, i) => ({
  id: i,
  name: "Chicken Biryani",
  desc: "Aromatic basmati rice cooked with spices.",
  price: 290 + i * 10,
}));
</script>

<style scoped>
/* =====================
   LAYOUT
===================== */
.order-page {
  padding: 40px 0;
  background: #f7f7f7;
}

.order-layout {
  display: grid;
  grid-template-columns: 1fr 360px;
  gap: 32px;
}

/* =====================
   HEADER
===================== */
.order-header {
  background: #63a772;
  padding: 28px;
  border-radius: 14px;
  margin-bottom: 24px;
 display: flex;               /* ✅ required */
  flex-direction: column;      /* stack h1 & p */
  justify-content: center;     /* vertical center */
  align-items: center;         /* horizontal center */
  text-align: center;          /* text alignment */
  height: 200px;
}

.order-header h1 {
  font-size: 28px;
  margin-bottom: 8px;
}

.order-header p {
 color:#fff;
}

/* =====================
   SEARCH + FILTER
===================== */
.menu-actions {
  display: flex;
  gap: 12px;
  margin-bottom: 16px;
}

.menu-actions input {
  flex: 1;
  padding: 12px 14px;
  border-radius: 20px;
  border: 1px solid #ddd;
}

.filter-btn {
  padding: 0 18px;
  border-radius: 20px;
  border: none;
  background: #63a772;
  color: #fff;
}

/* =====================
   CATEGORY SLIDER
===================== */
.category-slider {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 20px;
}

.category-track {
  display: flex;
  gap: 12px;
  overflow-x: auto;
  scroll-behavior: smooth;
}

.category-track span {
  white-space: nowrap;
  background: #fff;
  padding: 8px 14px;
  border-radius: 20px;
  font-size: 14px;
}

.slide-btn {
  border: none;
  background: #fff;
  width: 32px;
  height: 32px;
  border-radius: 50%;
  cursor: pointer;
}

/* =====================
   FOOD GRID
===================== */
.food-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

.food-card {
  background: #fff;
  border-radius: 14px;
  overflow: hidden;
}

.food-card img {
  width: 100%;
  height: 160px;
  object-fit: cover;
}

.food-info {
  padding: 14px;
}

.food-info h3 {
  font-size: 16px;
}

.food-info p {
  font-size: 13px;
  color: #666;
  margin: 6px 0;
}

.food-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.food-bottom button {
  background: #63a772;
  border: none;
  color: #fff;
  padding: 6px 14px;
  border-radius: 16px;
}

/* =====================
   ORDER SUMMARY
===================== */
.order-summary {
  background: #eaf4ec;
  border-radius: 16px;
  padding: 20px;
  height: fit-content;
  position: sticky;
  top: 20px;
}

.summary-note {
  font-size: 13px;
  color: #555;
  margin-bottom: 16px;
}

.summary-list {
  max-height: 300px;
  overflow-y: auto;
}

.summary-item {
  display: flex;
  gap: 10px;
  margin-bottom: 12px;
}

.summary-item img {
  width: 50px;
  height: 50px;
  border-radius: 8px;
}

.confirm-btn {
  width: 100%;
  margin-top: 16px;
  padding: 12px;
  border-radius: 20px;
  background: #63a772;
  color: #fff;
  border: none;
}

/* =====================
   RESPONSIVE
===================== */
@media (max-width: 1024px) {
  .food-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .order-layout {
    grid-template-columns: 1fr;
  }

  .order-summary {
    position: static;
  }
}

@media (max-width: 600px) {
  .food-grid {
    grid-template-columns: 1fr;
  }

  .menu-actions {
    flex-direction: column;
  }
}
</style>
