<template>
  <footer class="footer">
    <div class="container footer-grid">
      <!-- LEFT -->
      <div class="footer-brand">
        <h2>Konaseema Ghumaghumalu</h2>
        <img src="/logo.png" alt="Konaseema Ghumaghumalu" />
        <p>
          Authentic Andhra flavors in the heart of KPHB, Hyderabad. Experience
          traditional coastal cuisine with a modern touch.
        </p>
        <span class="follow" style="font-weight: bolder;">FOLLOW US</span>

        <div class="footer-social">
          <a href="#"><Icon icon="mdi:facebook" /></a>
          <a href="#"><Icon icon="mdi:twitter" /></a>
          <a href="#"><Icon icon="mdi:instagram" /></a>
        </div>
      </div>

      <!-- MY ACCOUNT -->
      <div class="footer-col">
        <h5>MY ACCOUNT</h5>
        <ul>
          <li><NuxtLink to="#">Sign In</NuxtLink></li>
          <li><NuxtLink to="#">Create Your Account</NuxtLink></li>
          <li><NuxtLink to="#">My Account</NuxtLink></li>
        </ul>
      </div>

      <!-- MENU -->
      <div class="footer-col">
        <h5>MENU</h5>
        <ul>
          <li><NuxtLink to="#">Special Offers</NuxtLink></li>
          <li><NuxtLink to="#">Starters</NuxtLink></li>
          <li><NuxtLink to="#">Kids</NuxtLink></li>
          <li><NuxtLink to="#">Night Offers</NuxtLink></li>
          <li><NuxtLink to="#">Weekend Offer</NuxtLink></li>
        </ul>
      </div>

      <!-- RIGHT -->
      <div class="footer-col">
        <h5>ABOUT US</h5>
        <ul>
          <li><NuxtLink to="#">Store Locations</NuxtLink></li>
          <li><NuxtLink to="#">About Us</NuxtLink></li>
        </ul>
      </div>

      <div class="footer-col">
        <h5>LEARN MORE</h5>
        <ul>
          <li><NuxtLink to="#">Privacy Policy</NuxtLink></li>
          <li><NuxtLink to="#">Cookie Policy</NuxtLink></li>
          <li><NuxtLink to="#">Terms & Conditions</NuxtLink></li>
        </ul>
      </div>

      <div class="footer-col">
        <h5 >SERVICE</h5>
        <ul>
          <li><NuxtLink to="#">Contact Us</NuxtLink></li>
          <li><NuxtLink to="#">FAQs</NuxtLink></li>
        </ul>
      </div>
      
    </div>

    <div class="footer-bottom">
      <span>© 2025 Konaseema Ghumaghumalu. All rights reserved.</span>
      <span>
        konaseema.restro@gmail.com | +91 7674800999 | KPHB, Hyderabad
      </span>
    </div>
  </footer>
</template>

<script setup>
import { Icon } from "@iconify/vue";
</script>

<style scoped>
.footer {
  background: var(--footer-bg);
}

.footer-grid {
  display: grid;
  grid-template-columns: 1.5fr repeat(5, 1fr);
  gap: 40px;
  padding: 40px 0;
}

/* LEFT */
.footer-brand img {
  height: 70px;
  margin-bottom: 14px;
}

.footer-brand p {
  font-size: 15px;
  font-weight: 500;
  line-height: 1.9;
  max-width: 380px; 
}

.follow {
  display: block;
  margin-top: 17px;
  color: var(--text);
  font-size: 15px;
}

/* SOCIAL */
.footer-social {
  display: flex;
  gap: 12px;
  margin-top: 16px;
}

.footer-social a {
  width: 32px;
  height: 32px;
  background: #7c9a84;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
}

/* COLUMNS */
.footer-col h5 {
  font-size: 17px;
  font-weight: bold; /* section label */
  margin-bottom: 14px;
}

.footer-col ul {
  list-style: none;
  padding: 0;
}

.footer-col li {
  margin-bottom: 11px;
}

.footer-col a {
  text-decoration: none;
  color: var(--text);
  font-size: 15px;
  font-weight: 500; /* medium text like design */
}

.footer-col a:hover {
  color: var(--accent);
}

.mt {
  margin-top: 16px;
}

/* BOTTOM BAR */
.footer-bottom {
  margin-top: 40px;
  background: #7c9a84;
  color: #fff;
  padding: 12px 24px;
  display: flex;
  justify-content: space-between;
  font-size: 14px;
  flex-wrap: wrap;
}

/* RESPONSIVE */
@media (max-width: 1200px) {
  .footer-grid {
    padding: 0px 30px 0px 30px;
  }
}
@media (max-width: 900px) {
  .footer-grid {
    grid-template-columns: 1fr 1fr;
  }
}

@media (max-width: 600px) {
  .footer-grid {
    grid-template-columns: 1fr;
  }

  .footer-bottom {
    text-align: center;
    justify-content: center;
    gap: 6px;
  }
}
</style>
