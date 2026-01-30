<template>
  <header class="site-header">
    <div class="container header-bar">
      <!-- LEFT : LOGO -->
      <div class="header-left">
        <img src="/logo.png" alt="Konaseema Ghumaghumalu" />
        <div class="brand-text">
          <h4 class="brand-title">Konaseema</h4>
          <h4 class="brand-sub">Ghumaghumalu</h4>
        </div>
      </div>

      <!-- CENTER : OPTIONS -->
      <div class="header-center">
        <NuxtLink to="/orderPage" class="mode-btn" active-class="active">
          <img src="/images/delivery.svg" alt="Delivery" />
          Delivery
        </NuxtLink>

        <button class="mode-btn">
          <img src="/images/dining.svg" alt="Dining" />
          Dining
        </button>

        <button class="mode-btn">
          <img src="/images/catering.svg" alt="Catering" />
          Catering
        </button>

        <button class="mode-btn">
          <img src="/images/pickup.svg" alt="Pickup" />
          Pickup
        </button>
      </div>
      <!-- RIGHT : SEARCH + ICONS -->
      <div class="header-right">
        <div class="search-box">
          <Icon icon="si:search-line" />
          <input type="text" placeholder="Search Item" />
        </div>

        <Icon icon="mdi:cart-outline" class="icon-btn" />
        <Icon icon="mdi:menu" class="icon-btn" />
      </div>
    </div>
  </header>
</template>

<script setup>
import { Icon } from "@iconify/vue";
</script>

<style scoped>
.site-header {
  position: sticky;
  top: 0;
  z-index: 1000;
  background: #fff;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.06);
}

.header-bar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 14px;
}

/* LEFT */
.header-left {
  display: flex;
  align-items: center;
  gap: 10px;
}

.header-left img {
  height: 42px;
}

.brand-text {
  display: flex;
  flex-direction: column;
  line-height: 1.1;
}

.brand-title {
  font-size: 18px;
  color: #284730;
}

.brand-sub {
  font-size: 18px;
  color: #284730;
}

/* CENTER */
.header-center {
  display: flex;
  gap: 14px;
}

.mode-btn {
  display: flex;
  align-items: center;
  gap: 6px;
  padding: 8px 14px;
  background: #f3f4f6;
  border-radius: 12px;
  border: 1px solid #00000024;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;

  color: #333;
  text-decoration: none;
  transition: all 0.2s ease;
}

/* Hover */
.mode-btn:hover {
  background: #ffedd5; /* light orange */
  color: #c2410c;
  border-color: #fdba74;
}

/* Active / Selected */
.mode-btn.active {
  background: #FF7F50; /* dark orange */
  color: #000;
  border-color: #ea580c;
}

/* Icon color follows text */
.mode-btn img {
  width: 18px;
  height: 18px;
}

.search-box img {
  width: 18px;
  height: 18px;
}

.icon-btn {
  width: 22px;
  height: 22px;
  cursor: pointer;
}

/* RIGHT */
.header-right {
  display: flex;
  align-items: center;
  gap: 14px;
}

.search-box {
  display: flex;
  align-items: center;
  gap: 6px;
  padding: 8px 12px;
  background: #f3f4f6;
  border-radius: 18px;
  border: 1px solid #00000024;
}

.search-box input {
  border: none;
  background: transparent;
  outline: none;
  font-size: 14px;
  width: 80px;
}

.icon-btn {
  font-size: 22px;
  cursor: pointer;
}

@media (max-width: 900px) {

}

/* RESPONSIVE */
@media (max-width: 900px) {
  .header-center {
    display: none;
  }

  /* .search-box input {
    width: 100px;
  } */
  .search-box{
        display: none;

  }
}
</style>
