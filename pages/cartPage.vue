<template>
  <section class="cart-page">
    <div class="container cart-layout">
      <!-- LEFT -->
      <div class="cart-left">
        <h2 class="page-title">Review Your Order</h2>

        <!-- ITEMS -->
        <div class="cart-items">
          <div v-for="item in cart" :key="item.id" class="cart-item">
            <!-- FAVORITE -->
            <button class="cart-fav-btn" @click="item.fav = !item.fav">
              <Icon
                :icon="item.fav ? 'mdi:heart' : 'mdi:heart-outline'"
                :color="item.fav ? '#e11d48' : '#9ca3af'"
              />
            </button>
            <img :src="item.image" />

            <div class="cart-info">
              <h4>{{ item.name }}</h4>
              <p>{{ item.desc }}</p>

              <div class="price-row">
                <span class="main-price">₹{{ item.price }}</span>
                <span class="qtn-price">
                  (₹{{ item.price }} × {{ item.qty }} Quantity)
                </span>
              </div>
            </div>

            <div class="cart-actions">
              <button
                v-if="item.qty > 1"
                class="icon-btn minus"
                @click="decrease(item)"
              >
                <Icon icon="mdi:minus" />
              </button>

              <button v-else class="icon-btn danger" @click="remove(item)">
                <Icon icon="mingcute:delete-fill" />
              </button>

              <span class="qty">{{ item.qty }}</span>

              <button class="icon-btn" @click="increase(item)">
                <Icon icon="mdi:plus" />
              </button>
            </div>
          </div>
        </div>

        <!-- DELIVERY INSTRUCTIONS -->
        <div class="delivery-box">
          <h4>Delivery Instructions <span>(optional)</span></h4>

          <textarea
            placeholder="Provide clear directions or special notes for the delivery partner"
          ></textarea>

          <div class="delivery-footer">
            <label>
              <input type="checkbox" />
              Save your delivery notes for faster checkout
            </label>

            <button class="btn-primary small">Done</button>
          </div>
        </div>
      </div>

      <!-- RIGHT -->
      <div class="cart-right">
        <h2>Order Summary</h2>
        <p class="summary-desc">
          A clear overview of your order, giving you complete transparency on
          items, pricing, and totals before confirmation.
        </p>

        <div class="summary-card">
          <!-- ADDRESS -->
          <div class="address-box">
            <div>
              <h4>We'll deliver your order here</h4>
              <p>
                Flat No. 203, Green Meadows Apartments, Madhapur, Hyderabad –
                500081
              </p>
              <button class="link-btn" style="margin-top: 10px">Change</button>
            </div>
            <img src="/images/location.png" alt="Location" class="sum-icon" />
          </div>

          <!-- PROMO -->
          <div class="promo-box">
            <div>
              <h4>Don’t Miss Extra Savings</h4>
              <p>Enter your promo code below</p>

              <div class="promo-input">
                <input type="text" placeholder="Promo Code" />
                <button class="apply-btn">Apply</button>
              </div>
            </div>
            <img src="/images/ticket.png" alt="Ticket" class="sumt-icon" />
          </div>

          <!-- PRICE -->
          <div class="price-summary">
            <div>
              <span style="font-size: 15px; font-weight: 500">Subtotal</span>
              <span style="font-size: 15px; font-weight: 600"
                >₹{{ subtotal }}</span
              >
            </div>
            <div>
              <span style="font-size: 15px; font-weight: 500">Tax & Fees</span>
              <span style="font-size: 15px; font-weight: 600">₹{{ tax }}</span>
            </div>
            <div>
              <span style="font-size: 15px; font-weight: 500">Delivery</span>
              <span style="font-size: 15px; font-weight: 600"
                >₹{{ delivery }}</span
              >
            </div>

            <hr />

            <div class="total">
              <strong>Total</strong>
              <strong>₹{{ total }}</strong>
            </div>
          </div>

          <button class="btn-primary checkout-btn">Checkout</button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Icon } from "@iconify/vue";
import { ref, onMounted, computed, watch } from "vue";

const cart = ref([]);

onMounted(() => {
  const saved = localStorage.getItem("order-cart");
  if (saved) cart.value = JSON.parse(saved);
});

watch(cart, (v) => localStorage.setItem("order-cart", JSON.stringify(v)), {
  deep: true,
});

function increase(item) {
  item.qty++;
}
function decrease(item) {
  if (item.qty > 1) item.qty--;
}
function remove(item) {
  cart.value = cart.value.filter((i) => i.id !== item.id);
}

/* PRICES */
const subtotal = computed(() =>
  cart.value.reduce((s, i) => s + i.price * i.qty, 0),
);
const tax = computed(() => Math.round(subtotal.value * 0.12));
const delivery = 40;
const total = computed(() => subtotal.value + tax.value + delivery);
</script>

<style scoped>
.cart-page {
  padding: 40px 0;
  line-height: 1.7;
}

.cart-layout {
  display: grid;
  grid-template-columns: 2.2fr 1fr;
  gap: 32px;
}

/* LEFT */
.page-title {
  margin-bottom: 20px;
}

.cart-items {
  display: flex;
  flex-direction: column;
  gap: 16px;

  max-height: 65vh; /*  controls visible height */
  overflow-y: auto; /*  enables scroll */
  padding-right: 6px; /* prevents content cut */
}

.cart-item {
  display: flex;
  /* gap: 16px; */
  background: #fff;
  border-radius: 16px;
  border: 1px solid #e5e7eb;
}

.cart-item {
  position: relative; /* 🔥 needed for absolute heart */
}

/* FAVORITE BUTTON */
.cart-fav-btn {
  position: absolute;
  top: 10px;
  right: 10px;

  background: #fff;
  border: none;
  border-radius: 50%;
  width: 32px;
  height: 32px;

  display: flex;
  align-items: center;
  justify-content: center;

  cursor: pointer;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.08);
}


.cart-item img {
  width: 200px;
  border-radius: 16px 0 0 16px;
}

.cart-info {
  padding: 12px;
}

.cart-info p {
  font-size: 13px;
  color: #6b7280;
}

.price-row {
  margin-top: 26px;
  font-size: 14px;
}
.main-price {
  font-weight: 600;
  font-size: 15px;
  color: #418855;
}

.qtn-price {
  font-size: 14px;
  color: #418855;
  padding-left: 6px;
}

.cart-actions {
  margin-left: auto;
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 12px;
}

/* DELIVERY BOX */
.delivery-box {
  margin-top: 24px;
  background: #f1f7f3;
  border-radius: 16px;
  padding: 16px;
}

.delivery-box textarea {
  width: 100%;
  min-height: 80px;
  margin-top: 8px;
  border-radius: 12px;
  padding: 10px;
  border: 1px solid #d1d5db;
  font-family: Inter, sans-serif;
}

.delivery-footer {
  display: flex;
  justify-content: space-between;
  margin-top: 12px;
}

/* RIGHT */
.cart-right .summary-card {
  background: #e1ebe4;
  border-radius: 18px;
  padding: 20px;
}

.cart-right h2 {
  font-size: 18px;
  margin-bottom: 8px;
}

.summary-desc {
  font-size: 14px;
  color: #6b7280;
  margin-bottom: 10px;
}
.address-box,
.promo-box {
  display: flex;
  gap: 12px;
  margin-bottom: 26px;
}

.promo-box {
  padding-top: 26px;
}

.address-box h4 {
  color: #418855;
  margin-bottom: 4px;
  font-family: Inter;
}
.address-box p {
  font-size: 14px;
  color: #6b7280;
  margin-bottom: 6px;
}

.promo-box {
  margin-top: 40px;
  border-radius: 20px;
}

.sum-icon {
  width: 80px;
  height: auto;
  color: #bed9c5;
}

.sumt-icon {
  width: 80px;
  height: auto;
  color: #bed9c5;
}

.promo-box h4 {
  color: #418855;
  margin-bottom: 4px;
  font-family: Inter;
}
.promo-box p {
  font-size: 14px;
  color: #6b7280;
  margin-bottom: 6px;
}

.promo-input {
  position: relative;
  margin-top: 8px;
}

.promo-input input {
  width: 100%;
  padding: 12px 90px 12px 14px; /* space for button */
  border-radius: 30px;
  border: 1px solid #d1d5db;
  font-size: 14px;
}

.apply-btn {
  position: absolute;
  right: 6px;
  top: 50%;
  transform: translateY(-50%);
  background: #5fa974;
  color: #fff;
  border: none;
  padding: 8px 20px;
  border-radius: 20px;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
}

.link-btn {
  background: #5fa974;
  color: #fff;
  padding: 8px 25px;
  border-radius: 25px;
  /* margin-top: 10px; */
  font-weight: 500;
  font-size: 16px;
  border: none;
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  text-decoration: none;
  box-shadow: 0 8px 20px var(--button-shadow);
  transition: all 0.3s ease;
}

.price-summary div {
  display: flex;
  justify-content: space-between;
  margin: 6px 0;
  line-height: 1.9;
}

.total {
  font-size: 18px;
  margin-top: 10px;
}

.checkout-btn {
  width: 100%;
  margin-top: 16px;
}

/* ICON BUTTONS */
.icon-btn {
  width: 26px;
  height: 26px;
  border-radius: 50%;
  background: #5fa974;
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  border: none; /* ✅ force remove */
}

.icon-btn.minus {
  background: transparent;
  border: 1px solid #5fa974; /* ✅ only minus */
  color: #5fa974;
}

.icon-btn.danger {
  background: #dc2626;
  border: none; /* ✅ ensure no border */
  color: #fff;
}

/* RESPONSIVE */
@media (max-width: 1024px) {
  .cart-layout {
    grid-template-columns: 1fr;
  }
}
@media (max-width: 764px) {
  .sum-icon {
    width: 90px;
    height: auto;
    color: #bed9c5;
  }

  .sumt-icon {
    width: 80px;
    height: auto;
  }
}
</style>
