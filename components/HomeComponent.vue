<template>
  <!-- Trending now -->
  <section class="trending-section">
    <div class="container trending-layout">
  
      <!-- LEFT CONTENT -->
      <div class="trending-content">
        <h3 class="trending-subtitle">WHAT THEY SAY</h3>
        <h1 class="trending-title">What Our Customers Say About Us!</h1>

        <p class="trending-desc">
          “Fudo is the best. Besides the many and delicious meals, the service
          is also very good, especially in the very fast delivey. I highly
          recommend Fudo to you”.
        </p>
       <!-- RIGHT COLUMN : REVIEWS -->
    <div class="testimonial-right">

      <!-- MAIN REVIEW -->
      <div class="review-card">
        <img src="/images/swetha.jpg" alt="user" class="review-avatar" />

        <div class="review-info">
          <span class="review-name">Deepika Choudary</span>
          <span class="review-role">Food Enthusiast</span>
          <div class="stars">★★★★★ <span>4.8</span></div>
        </div>
      </div>
                <span style="font-weight: 500;">Our Reviews</span>

      <!-- USERS STACK -->
      <div class="review-users">
        <img src="/images/swetha.jpg" alt="user" />
        <img src="/images/swetha.jpg" alt="user" />
        <img src="/images/swetha.jpg" alt="user" />

        <!-- 4th user with count -->
        <div class="more-users">+12</div>
      </div>

    </div>
      </div>

      <!-- RIGHT IMAGE -->
      <div class="trending-image">
        <div class="image-ring">
          <NuxtImg
            src="/images/chef.png"
            alt="Trending dental care"
            format="webp"
          />
        </div>
      </div>
    </div>
  </section>

  <!-- Doctor section -->
  <section id="doctors" class="doctors-section">
    <div class="container">
      <div class="doctors-header">
        <h3 class="trending-subtitle">EXPLORE OUR CATEGORIES</h3>
        <h1>Discover Delicious Options Curated Just For You</h1>
      </div>

      <div class="doctors-grid">
        <div v-for="doctor in doctors" :key="doctor.id" class="doctor-card">
          <NuxtImg
            :src="doctor.image"
            :alt="doctor.name"
            class="doctor-image"
            format="webp"
          />
          <h3>{{ doctor.name }}</h3>
          <span class="doctor-span">{{ doctor.designation }}</span>
        </div>
      </div>
    </div>
  </section>

  <!-- Trending now -->
  <section class="testimonial-section">
    <div class="container trending-layout">
      <!-- LEFT IMAGE -->
      <div class="trending-image">
        <div class="image-ring">
          <NuxtImg
            src="/images/appimg.png"
            alt="Trending dental care"
            format="webp"
          />
        </div>
      </div>
      <!-- RIGHT CONTENT -->
      <div class="trending-content">
        <h3 class="trending-subtitle">DOWNLOAD APP</h3>
        <h1 class="trending-title">Get Started With Konaseema App Tod</h1>

        <p class="trending-desc">
          Discover food wherever and whenever and get your food delivered
          quickly.
        </p>
        <button class="btn-primary">Get The App</button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted, onBeforeUnmount } from "vue";
import { Icon } from "@iconify/vue";

let lastScrollY = 0;

onMounted(() => {
  const elements = document.querySelectorAll(
    ".animate-vertical, .animate-left",
  );

  const observer = new IntersectionObserver(
    (entries) => {
      const currentScrollY = window.scrollY;
      const scrollingDown = currentScrollY > lastScrollY;

      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          if (entry.target.classList.contains("animate-vertical")) {
            entry.target.classList.toggle("from-bottom", scrollingDown);
            entry.target.classList.toggle("from-top", !scrollingDown);
          }

          entry.target.classList.add("animate-in");
        } else {
          entry.target.classList.remove("animate-in");
        }
      });

      lastScrollY = currentScrollY;
    },
    {
      threshold: 0.2,
    },
  );

  elements.forEach((el) => observer.observe(el));

  onBeforeUnmount(() => observer.disconnect());
});

const doctors = [
  {
    id: 1,
    name: "Soup",
    image: "/images/soup.png",
  },
  {
    id: 2,
    name: "Starter",
    image: "/images/soup.png",
  },
  {
    id: 3,
    name: "Biryani",
    image: "/images/soup.png",
  },

  {
    id: 4,
    name: "Pulao",
    image: "/images/soup.png",
  },
  {
    id: 5,
    name: "Noodles",
    image: "/images/soup.png",
  },
  {
    id: 6,
    name: "Fried Rice",
    image: "/images/soup.png",
  },
  {
    id: 7,
    name: "Mocktails",
    image: "/images/soup.png",
  },
  {
    id: 8,
    name: "Curries",
    image: "/images/soup.png",
  },
];
</script>

<style scoped>
/* =========================
   FEATURES SECTION
========================= */
.features-section {
  padding: 64px 0;
  background: #fff;
}

/* grid only — container already handled globally */
.features-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 18px;
  text-align: center;
}

/* card */
.feature-card h2 {
  margin-bottom: 10px;
  color: var(--text);
}

.feature-card p {
  font-size: 16px;
  line-height: 1.7;
  color: #484848;
}

/* =========================
   FEATURE CARD
========================= */
.feature-card {
  background: #ffffff;
  border: 1px solid #1cb99e;
  border-radius: 12px;
  padding: 32px 26px;

  /* neat layered shadow */
  box-shadow:
    0 2px 6px rgba(0, 0, 0, 0.05),
    0 10px 20px rgba(0, 0, 0, 0.06);

  transition:
    transform 0.25s ease,
    box-shadow 0.25s ease;
}

/* Hover – subtle lift, not aggressive */
.feature-card:hover {
  transform: translateY(-4px);
  box-shadow:
    0 6px 14px rgba(0, 0, 0, 0.08),
    0 16px 32px rgba(0, 0, 0, 0.1);
}

/* icon */
.feature-icon {
  font-size: 42px;
  color: var(--accent);
  margin-bottom: 5px;
}

/* =========================
   RESPONSIVE
========================= */
@media (max-width: 900px) {
  .features-grid {
    grid-template-columns: 1fr;
    gap: 36px;
  }
}

/* =========================
   TRENDING SECTION
========================= */
.trending-section {
  padding:0 70px 0 70px;
  overflow-x: hidden; /* prevents white space */
}

.trending-layout {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 64px;
  align-items: center;
}

/* LEFT IMAGE */
.trending-image {
  display: flex;
  justify-content: center;
}

.image-ring {
  width: 100%;
  max-width: 500px;
}

.image-ring img {
  width: 100%;
  height: auto;
  object-fit: cover;
}

/* RIGHT CONTENT */
.trending-title {
  font-size: 38px;
  font-weight: 700;
  margin-bottom: 8px;
}

.trending-subtitle {
  font-size: 20px;
  color: #159038;
  margin-bottom: 20px;
  font-family: "Inter", sans-serif;
}

.trending-desc {
  font-size: 16px;
  line-height: 1.7;
  margin-bottom: 28px;
}

/* POINTS LIST */
.trending-points {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.trending-points li {
  display: flex;
  gap: 16px;
}

.trending-points h3 {
  font-size: 24px;
  margin-bottom: 4px;
}

.trending-points p {
  font-size: 16px;
  line-height: 1.6;
}

/* ICONS */
.trending-points .icon {
  min-width: 46px;
  height: 46px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-size: 25px;
}

.icon.teal {
  background: #1cb99e;
}
.icon.blue {
  background: #4f8fc4;
}
.icon.navy {
  background: #243b6b;
}
.icon.dark {
  background: #1f2f5c;
}

/* =========================
   RESPONSIVE
========================= */
@media (max-width: 900px) {
  .trending-layout {
    grid-template-columns: 1fr;
    gap: 40px;
  }

  .image-ring {
    max-width: 520px;
  }
}

.missing {
  text-align: center;
  max-width: 900px; /* optional, looks better */
  margin: 0 auto 40px; /* centers + spacing below */
  color: var(--text);
  font-size: 38px;
}
/* =========================
   DOCTORS SECTION
========================= */
.doctors-section {
  padding: 80px 0;
}

.doctors-header {
  text-align: center;
  margin-bottom: 48px;
}

.doctors-header h1 {
  font-size: 38px;
  font-weight: 700;
  margin-bottom: 12px;
}

.doctors-header p {
  font-size: 18px;
  color: #555;
  max-width: 720px;
  margin: 0 auto;
}

/* 4 doctors in a row */
.doctors-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 28px;
}

.doctor-card {
  text-align: center;
  transition:
    transform 0.25s ease,
    box-shadow 0.25s ease;
}

/* .doctor-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 14px 32px rgba(0, 0, 0, 0.12);
} */

.doctor-image {
  width: 100%;
  height: auto;
  object-fit: contain;
  border-radius: 14px;
  margin-bottom: 16px;
}

.doctor-card h3 {
  font-size: 20px;
  margin-bottom: 6px;
  color: #0e7b2d;
}
.doctor-card h3:hover {
  color: #1cb99e;
}

.doctor-span {
  display: block;
  font-size: 14px;
  color: #5b5b5b;
  margin-bottom: 26px;
}

/* =========================
   RESPONSIVE
========================= */
@media (max-width: 1024px) {
  .doctors-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
  .doctors-grid {
    grid-template-columns: 1fr;
  }
}

.appointment-section {
  padding: 100px 0;
  background: #ffffff;
}

.appointment-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 5px;
  align-items: center;
}

/* LEFT */
.appointment-left h1 {
  font-size: 38px;
  font-weight: 700;
  line-height: 1.3;
}

.divider {
  display: block;
  width: 60px;
  height: 4px;
  background: var(--accent);
  margin: 20px 0;
}

.appointment-left p {
  font-size: 24px;
  font-weight: 500;
  line-height: 1.4;
}

/* RIGHT */
.appointment-right {
  background: #fff;
}

.emergency-text {
  font-size: 14px;
  font-weight: 600;
  color: #333;
}

.appointment-right h1 {
  font-size: 38px;
  margin: 10px 0 30px;
}

.appointment-right h1 span {
  color: var(--accent);
}

/* FORM */
.appointment-form {
  display: flex;
  flex-direction: column;
  gap: 18px;
  border: 1px solid rgb(218, 216, 216);
  padding: 10px;
  border-radius: 10px;
}

.appointment-form input,
.appointment-form select,
.appointment-form textarea {
  width: 100%;
  padding: 14px 16px;
  border: 1px solid #eee;
  border-radius: 8px;
  font-size: 15px;
  outline: none;
}

.appointment-form textarea {
  resize: none;
  height: 120px;
}
.appointment-form input,
.appointment-form select,
.appointment-form textarea,
.appointment-form button {
  font-family: "Roboto", sans-serif;
}

.two-col {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.appointment-submit {
  display: inline-flex;
  align-items: center; /* vertical center */
  justify-content: center; /* horizontal center */
  gap: 10px;

  height: 52px; /* fixed height avoids drift */
  padding: 0 28px;

  background: #1f2f5c;
  color: #fff;
  border-radius: 8px;
  border: none;

  font-size: 16px;
  font-weight: 500;
  line-height: 1;
  cursor: pointer;
}

.appointment-submit span {
  display: inline-flex;
  align-items: center;
}

.tick-icon {
  font-size: 20px;
  line-height: 1;
}

.appointment-form button:hover {
  opacity: 0.9;
}

/* RESPONSIVE */
@media (max-width: 900px) {
  .appointment-grid {
    grid-template-columns: 1fr;
    gap: 60px;
  }

  .appointment-left,
  .appointment-right {
    text-align: center;
  }

  .divider {
    margin: 20px auto;
  }

  .two-col {
    grid-template-columns: 1fr;
  }
}

.testimonial-section {
  padding: 15px 0;
  margin: 78px;
  border-radius: 20px;
  background-color: #89bd9780;
  overflow-x: hidden; /* prevents white space */
}
/* =========================
   TESTIMONIAL GRID
========================= */
.testimonial-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
}

/* LEFT */
.testimonial-text {
  margin-top: 20px;
  line-height: 1.7;
}

/* RIGHT */
.testimonial-right {
  display: flex;
  flex-direction: column;
  gap: 28px;
}

/* REVIEW CARD */
.review-card {
  display: flex;
  align-items: center;
  gap: 16px;
}

.review-avatar {
  width: 64px;
  height: 64px;
  border-radius: 50%;
  object-fit: cover;
}

.review-info {
  display: flex;
  flex-direction: column;
}

.review-name {
  font-weight: bold;
}

.review-role {
  font-size: 12px;
  color: lightslategray;
  margin: 2px 0 6px;
}

.stars {
  color: #f5b400;
  font-size: 14px;
}

.stars span {
  color: #333;
  margin-left: 6px;
}

/* USERS STACK */
.review-users {
  display: flex;
  align-items: center;
}

.review-users img,
.more-users {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: 2px solid #fff;
  margin-left: -15px;
  cursor: pointer;
  transition: transform 0.3s ease;
}

.review-users img:hover,
.more-users:hover {
  transform: translateY(-4px);
}

/* 4th USER */
.more-users {
  background: #159038;
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 13px;
  font-weight: bold;
}

/* RESPONSIVE */
@media (max-width: 900px) {
  .testimonial-grid {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .review-card {
    justify-content: center;
  }

  .review-users {
    justify-content: center;
  }
}

/* =========================
   SCROLL ANIMATIONS
========================= */
.animate-vertical,
.animate-left {
  opacity: 0;
  transition:
    transform 0.9s cubic-bezier(0.22, 1, 0.36, 1),
    opacity 0.6s ease;
  will-change: transform, opacity;
}

/* Vertical directions */
.animate-vertical.from-bottom {
  transform: translateY(70px);
}

.animate-vertical.from-top {
  transform: translateY(-70px);
}

/* Left to right */
.animate-left {
  transform: translateX(-80px);
}

/* Active state */
.animate-in {
  opacity: 1;
  transform: translate(0, 0);
}
</style>
