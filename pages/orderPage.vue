<template>
  <section class="order-page">
    <div class="container">
      <!-- TOP BANNER -->
      <div class="order-banner">
        <h2>Place Your Order</h2>
        <p>
          Place your order in just a few easy steps, delivering freshly prepared
          dishes with consistent quality and on-time service.
        </p>
      </div>

      <!-- MAIN LAYOUT -->
      <div class="order-layout">
        <!-- LEFT SIDE -->
        <div class="order-left">
          <!-- SEARCH + FILTER -->
          <div class="order-controls">
            <!-- LEFT: SEARCH -->
            <div class="search-wrapper">
              <Icon icon="iconamoon:search-light" class="search-icon" />
              <input type="text" placeholder="Search Category or Menu" />
            </div>

            <!-- RIGHT: COUNT + FILTER -->
            <div class="controls-right">
              <span class="item-count">
                {{ items.length }} items are listed bellow
              </span>

              <button class="filter-btn">
                <Icon icon="mdi:filter-variant" class="filter-icon" />
                <span>Filter</span>
              </button>
            </div>
          </div>

          <div class="categories no-scrollbar">
            <button
              v-for="cat in categories"
              :key="cat.name"
              class="category-btn"
              :class="{ active: cat.name === selectedCategory }"
              @click="selectedCategory = cat.name"
            >
              <img :src="cat.image" :alt="cat.name" />
              <span>{{ cat.name }}</span>
            </button>
          </div>

          <!-- ITEMS GRID -->
          <div class="items-grid no-scrollbar">
            <div v-for="item in items" :key="item.id" class="item-card">
              <span class="rating">
                <Icon icon="ic:round-star" />
                4.8
              </span>

              <button class="fav-btn" @click="item.fav = !item.fav">
                <Icon
                  :icon="item.fav ? 'mdi:heart' : 'mdi:heart-outline'"
                  :color="item.fav ? '#e11d48' : '#555'"
                />
              </button>

              <img :src="item.image" :alt="item.name" />

              <div class="container">
                <h4>{{ item.name }}</h4>
                <p>{{ item.desc }}</p>

                <div class="item-bottom">
                  <span class="price">₹{{ item.price }}</span>

                  <!-- IF NOT IN CART -->
                  <button
                    v-if="!getCartItem(item)"
                    class="add-btn"
                    @click="addToCart(item)"
                  >
                    Add
                  </button>

                  <!-- IF IN CART -->
                  <div v-else class="qty">
                    <button
                      v-if="getCartItem(item).qty > 1"
                      @click="decrease(getCartItem(item))"
                      class="icon-btn minus"
                    >
                      <Icon icon="mdi:minus" />
                    </button>

                    <button
                      v-else
                      @click="remove(getCartItem(item))"
                      class="icon-btn danger"
                    >
                      <Icon icon="mingcute:delete-fill" />
                    </button>

                    <span>{{ getCartItem(item).qty }}</span>

                    <button
                      @click="increase(getCartItem(item))"
                      class="icon-btn"
                    >
                      <Icon icon="mdi:plus" />
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- RIGHT SIDE -->
        <div class="order-right-wrapper">
          <!-- OUTSIDE CARD HEADER -->
          <div class="order-right-header">
            <h3>Order Summary</h3>
            <p class="summary-desc">
              A clear overview of your order, giving you complete transparency
              on items, pricing, and totals before confirmation.
            </p>
          </div>

          <!-- CARD -->
          <div class="order-right">
            <!-- CARD HEADER -->
            <div class="chosen-header">
              <h4>Chosen Items</h4>
              <span class="chosen-count">
                {{ totalSelectedCount }}
                {{ totalSelectedCount === 1 ? "item" : "items" }}
              </span>
            </div>

            <div class="summary-items no-scrollbar">
              <div v-for="item in cart" :key="item.id" class="summary-item">
                <!-- IMAGE -->
                <img :src="item.image" />

                <!-- INFO -->
                <div class="summary-info">
                  <h5>{{ item.name }}</h5>
                  <p class="summary-desc">{{ item.desc }}</p>
                  <span class="price">₹{{ item.price }}</span>
                </div>

                <!-- ACTIONS -->
                <div class="summary-actions">
                  <!-- ❌ DELETE ICON -->
                  <button class="close-btn" @click="remove(item)">
                    <Icon icon="mdi:close" />
                  </button>

                  <!-- QTY CONTROLS -->
                  <div class="qty">
                    <button
                      v-if="item.qty > 1"
                      @click="decrease(item)"
                      class="icon-btn minus"
                    >
                      <Icon icon="mdi:minus" />
                    </button>

                    <button
                      v-else
                      @click="remove(item)"
                      class="icon-btn danger"
                    >
                      <Icon icon="mingcute:delete-fill" />
                    </button>

                    <span>{{ item.qty }}</span>

                    <button @click="increase(item)" class="icon-btn">
                      <Icon icon="mdi:plus" />
                    </button>
                  </div>
                </div>
              </div>
            </div>

            <NuxtLink to="/cartPage" class="btn-primary confirm-btn">
              Confirm Order
            </NuxtLink>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Icon } from "@iconify/vue";
import { ref, watch, onMounted, computed } from "vue";

const categories = [
  { name: "Biryani", image: "/images/biryani.jpg" },
  { name: "Appetizers", image: "/images/biryani.jpg" },
  { name: "Drinks", image: "/images/biryani.jpg" },
  { name: "Noodles", image: "/images/biryani.jpg" },
  { name: "Salad", image: "/images/biryani.jpg" },
  { name: "Desserts", image: "/images/biryani.jpg" },
  { name: "Seafood", image: "/images/biryani.jpg" },
  { name: "Vegetarian", image: "/images/biryani.jpg" },
];

const selectedCategory = ref("Biryani");

const items = ref([
  {
    id: 1,
    name: "Chicken Biryani",
    desc: "Aromatic rice with tender chicken & spices",
    price: 350,
    image: "/images/biryani.jpg",
    fav: false,
  },
  {
    id: 2,
    name: "Fried Chicken Biryani",
    desc: "Crispy fried chicken with rich masala",
    price: 390,
    image: "/images/biryani.jpg",
    fav: false,
  },
  {
    id: 3,
    name: "Prawns Biryani",
    desc: "Succulent prawns cooked in aromatic spices",
    price: 370,
    image: "/images/biryani.jpg",
    fav: false,
  },
  {
    id: 4,
    name: "Veg Biryani",
    desc: "Fragrant rice with mixed vegetables & spices",
    price: 300,
    image: "/images/biryani.jpg",
    fav: false,
  },
  {
    id: 5,
    name: "Mutton Biryani",
    desc: "Tender mutton pieces with flavorful rice",
    price: 450,
    image: "/images/biryani.jpg",
    fav: false,
  },

  {
    id: 6,
    name: "Egg Biryani",
    desc: "Boiled eggs with spiced rice & herbs",
    price: 320,
    image: "/images/biryani.jpg",
    fav: false,
  },
  {
    id: 7,
    name: "Dum Biryani",
    desc: "Slow-cooked biryani with rich flavors",
    price: 420,
    image: "/images/biryani.jpg",
    fav: false,
  },
  {
    id: 8,
    name: "Fry Piece Biryani",
    desc: "Crispy fried pieces with aromatic rice",
    price: 420,
    image: "/images/biryani.jpg",
    fav: false,
  },
  {
    id: 9,
    name: "Veg Biryani",
    desc: "Simple biryani with rich flavors",
    price: 320,
    image: "/images/biryani.jpg",
    fav: false,
  },
]);

const cart = ref([]);

onMounted(() => {
  const savedCart = localStorage.getItem("order-cart");
  if (savedCart) {
    cart.value = JSON.parse(savedCart);
  }
});

watch(
  cart,
  (val) => {
    if (process.client) {
      localStorage.setItem("order-cart", JSON.stringify(val));
    }
  },
  { deep: true },
);

function getCartItem(item) {
  return cart.value.find((i) => i.id === item.id);
}

function addToCart(item) {
  const found = cart.value.find((i) => i.id === item.id);
  if (found) {
    found.qty++;
  } else {
    cart.value.push({ ...item, qty: 1 });
  }
}

function increase(item) {
  item.qty++;
}

function decrease(item) {
  if (item.qty > 1) item.qty--;
}

function remove(item) {
  cart.value = cart.value.filter((i) => i.id !== item.id);
}

const totalSelectedCount = computed(() => {
  return cart.value.reduce((sum, item) => sum + item.qty, 0);
});

const summary = [
  {
    id: 1,
    name: "Fried Chicken Biryani",
    desc: "Crispy fried chicken with rich masala",
    price: 390,
    qty: 1,
    image: "/images/biryani.jpg",
  },
  {
    id: 2,
    name: "Paneer Curry",
    desc: "Creamy paneer curry with aromatic spices",
    price: 250,
    qty: 1,
    image: "/images/biryani.jpg",
  },
  {
    id: 3,
    name: "Veg Biryani",
    desc: "Simple biryani with rich flavors",
    price: 320,
    image: "/images/biryani.jpg",
  },
];
</script>

<style scoped>
.order-page {
  padding: 40px 0;
    line-height: 1.7;

}

/* BANNER */
.order-banner {
  background: #5fa974;
  padding: 28px;
  border-radius: 16px;
  margin-bottom: 32px;
  height: 200px;
  display: flex;
  flex-direction: column;
  justify-content: center; /* vertical center */
  align-items: center; /* horizontal center */
}

.order-banner h2 {
  font-size: 28px;
  margin-bottom: 8px;
  color: var(--text);
}
.order-banner p {
  color: #fff;
  /* max-width: 690px; */
  text-align: center;
}

/* LAYOUT */
.order-layout {
  display: grid;
  grid-template-columns: minmax(0, 3fr) minmax(0, 1.4fr);
  gap: 28px;
}

.order-left {
  min-width: 0; /* critical for grid layouts */
}

/* LEFT */
.order-controls {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 20px;
}

/* SEARCH INPUT WITH ICON */
.search-wrapper {
  position: relative;
  flex: 1;
}

.search-wrapper input {
  width: 100%;
  padding: 12px 16px 12px 44px; /* left space for icon */
  border-radius: 20px;
  border: 1px solid #ddd;
}

.search-icon {
  position: absolute;
  left: 16px;
  top: 50%;
  transform: translateY(-50%);
  font-size: 18px;
  color: #999;
  pointer-events: none;
}

.controls-right {
  display: flex;
  align-items: center;
  gap: 12px;
  white-space: nowrap;
}

/* ITEM COUNT TEXT */
.item-count {
  font-size: 13px;
  color: rgba(95, 169, 116, 0.8);
  font-weight: 500;
}

/* FILTER BUTTON */
.filter-btn {
  background: rgba(95, 169, 116, 0.8);
  color: #fff;
  border: 1px solid #ddd;
  border-radius: 20px;
  font-size: 14px;
  cursor: pointer;

  width: 90px;
  height: 35px;

  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;

  padding: 0;
}

.filter-icon {
  font-size: 16px;
}

.categories {
  display: flex;
  gap: 10px;
  flex-wrap: nowrap; /* keep single row */
  overflow-x: auto; /* enable horizontal scroll */
  overflow-y: hidden;
  padding-bottom: 16px; /* space for scrollbar */
  -webkit-overflow-scrolling: touch;
}
.categories :hover {
  background: #5fa974;
}
.category-btn {
  flex-shrink: 0; /* prevents button from shrinking */
}

.category-btn {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 4px 14px 4px 4px;
  border-radius: 24px;
  border: 1px solid #cbcbcb;
  background-color: #e1ebe4;
  cursor: pointer;
  font-size: 14px;
  font-weight: 500;
  white-space: nowrap;
}

.category-btn img {
  width: 32px;
  height: 32px;
  border-radius: 50%; /* 🔥 round image */
  object-fit: cover;
}

.category-btn.active {
  background: #0b653e;
  color: #fff;
  border-color: #0b653e;
}

/* .category-btn.active img {
  border: 2px solid #fff;
} */

/* ITEMS GRID */
.items-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  max-height: 95vh;
  overflow-y: auto;
}

.item-card {
  background: #fff;
  border-radius: 18px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.06);
  position: relative;
  border: 1px solid #dddddd;
}

.item-card img {
  width: 100%;
  border-radius: 18px 18px 0 0;
  margin-bottom: 10px;
}

.icon-btn {
  width: 26px;
  height: 26px;
  border-radius: 50%;
  background: #5fa974;
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

.icon-btn.danger {
  background: #df3e3e;
  color: #fff;
}

.icon-btn.minus {
  border: 1px solid #5fa974 !important;
  background: none !important;
  color: #5fa974;
}

.rating svg {
  color: #f5b400;
}

.rating {
  position: absolute;
  top: 12px;
  left: 12px;
  background: #fff;
  padding: 4px 8px;
  border-radius: 12px;
  font-size: 12px;
  font-weight: 600;
}

.fav-btn {
  position: absolute;
  top: 12px;
  right: 12px;
  border: none;
  background: #fff;
  border-radius: 50%;
  align-items: center;
  padding: 4px 6px;
  font-size: 16px;

  cursor: pointer;
}

.item-card h4 {
  font-size: 16px;
  margin-bottom: 4px;
}

.item-card p {
  font-size: 13px;
  color: #6b7280;
}

.item-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 12px 0px 12px 0px;
}

.price {
  font-weight: 700;
  color: var(--accent);
}

.add-btn {
  background: var(--accent);
  color: #fff;
  border: none;
  padding: 6px 14px;
  border-radius: 14px;
  cursor: pointer;
}

.order-right-wrapper {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.order-right-header h3 {
  font-size: 18px;
  margin-bottom: 4px;
}

.order-right-header .summary-desc {
  font-size: 13px;
  color: #6b7280;
}

/* RIGHT SUMMARY */
.order-right {
  background: #e1ebe4;
  padding: 20px;
  border-radius: 18px;
  height: fit-content;
  display: flex;
  flex-direction: column;
  max-height: 95vh;
}

.order-right .summary-desc {
  font-size: 13px;
  color: #6b7280;
  margin-top: 4px;
  margin-bottom: 14px;
}

.chosen-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 14px;
}

.chosen-header h4 {
  font-size: 15px;
  font-weight: 600;
  color: rgba(95, 169, 116, 0.9);
}

.chosen-count {
  font-size: 13px;
  color: rgba(95, 169, 116, 0.9);
  font-weight: 600;
}

.summary-items {
  flex: 1;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
  gap: 14px;
}

.summary-item {
  display: flex;
  gap: 12px;
  align-items: flex-start;
}

.summary-item img {
  width: 56px;
  height: 56px;
  border-radius: 12px;
  object-fit: cover;
  flex-shrink: 0;
}
.close-btn {
  background: transparent;
  border: none;
  color: #5fa974;
  cursor: pointer;
  font-size: 16px;
  padding: 2px;
}

.close-btn:hover {
  color: #df3e3e;
}

.summary-info h5 {
  font-size: 14px;
}

.summary-actions {
  margin-left: auto;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  gap: 6px;
}

.qty {
  margin-left: auto;
  display: flex;
  align-items: center;
  gap: 6px;
}

.qty button {
  width: 24px;
  height: 24px;
  border-radius: 50%;
  border: none;
  cursor: pointer;
}

.delete-btn {
  border: none;
  background: transparent;
  color: red;
  cursor: pointer;
}

.confirm-btn {
  width: 100%;
  margin-top: 20px;
  justify-content: center;
}

/* RESPONSIVE */
@media (max-width: 1024px) {
  .order-layout {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 768px) {
  .items-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 480px) {
  .items-grid {
    grid-template-columns: 1fr;
  }
}
</style>
