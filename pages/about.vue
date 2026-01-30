<template>
  <!-- TOP BANNER -->
  <section class="about-page">
    <div class="container">
      <div class="about-banner">
        <h2>About Konaseema Ghumaghumalu</h2>
        <p>
          Discover the story behind our passion for authentic Andhra cuisine and
          our commitment to preserving traditional flavors.
        </p>
      </div>
    </div>
  </section>

  <!-- ABOUT SECTION -->
  <section class="about-section">
    <div class="container about-layout">
      <!-- LEFT CONTENT -->
      <div class="about-content">
        <h2 class="section-title">Our Story</h2>

        <p class="section-desc">
          Konaseema Ghumaghumalu was born from a deep love for the authentic
          flavors of coastal Andhra Pradesh. Our journey began with a simple
          mission: to bring the traditional tastes of our homeland to food
          lovers in Hyderabad.
        </p>

        <p class="section-desc">
          Named after the beautiful Konaseema region, known for its rich
          culinary heritage, our restaurant celebrates the diverse and vibrant
          food culture of Andhra Pradesh. Every dish we serve tells a story of
          tradition, family recipes, and the warmth of Andhra hospitality.
        </p>

        <p class="section-desc">
          We believe that food is not just about taste, but about creating
          memories and bringing people together. Our chefs, trained in
          traditional cooking methods, use only the finest ingredients to ensure
          every meal is an authentic experience.
        </p>
      </div>

      <!-- RIGHT IMAGE -->
      <div class="about-image">
        <div class="image-ring">
          <NuxtImg src="/images/about.png" alt="Chef" format="webp" />
        </div>
      </div>
    </div>
  </section>

<!-- WHAT WE SERVE -->
<section class="serve-section">
  <div class="container">
    <h4 class="section-serve">WHAT WE SERVE</h4>
    <h2 class="section-heading">Your Favourite Food Delivery Partner</h2>

    <div class="serve-grid">
      <div class="serve-card">
        <img src="/images/easy-order.png" alt="Easy to Order" />
        <h4>Easy To Order</h4>
        <p>You only need a few steps in ordering food.</p>
      </div>

      <div class="serve-card">
        <img src="/images/fast-delivery.png" alt="Fast Delivery" />
        <h4>Fastest Delivery</h4>
        <p>Delivery that is always on time, even faster.</p>
      </div>

      <div class="serve-card">
        <img src="/images/best-quality.png" alt="Best Quality" />
        <h4>Best Quality</h4>
        <p>Not only fast, but quality is our number one priority.</p>
      </div>
    </div>
  </div>
</section>

<!-- KNOW OUR TEAM -->
<section class="team-section">
  <div class="container team-wrapper">
    <!-- HEADER ROW -->
    <div class="team-header-row">
      <div class="team-header-left">
        <span class="team-label">KNOW OUR TEAM</span>
        <h2 class="team-title">Meet Our Team</h2>
      </div>

      <p class="team-header-desc">
        Our passionate team of chefs and staff are dedicated to bringing you the
        best of Andhra cuisine.
      </p>
    </div>

    <!-- TEAM GRID -->
    <div class="team-grid">
      <!-- CARD 1 -->
      <div class="team-member">
        <img src="/images/ravi.png" alt="Chef Ravi Kumar" />

        <div class="member-card">
          <h4>Chef Ravi Kumar</h4>
          <span>HEAD CHEF</span>
          <p>20+ years of experience in traditional Andhra cuisine</p>
        </div>
      </div>

      <!-- CARD 2 -->
      <div class="team-member">
        <img src="/images/priya.png" alt="Priya Sharma" />

        <div class="member-card">
          <h4>Priya Sharma</h4>
          <span>RESTAURANT MANAGER</span>
          <p>Ensuring exceptional dining experiences for every guest</p>
        </div>
      </div>

      <!-- CARD 3 -->
      <div class="team-member">
        <img src="/images/venkat.png" alt="Venkat Reddy" />

        <div class="member-card">
          <h4>Venkat Reddy</h4>
          <span>OWNER & FOUNDER</span>
          <p>Passionate about sharing authentic Andhra flavors</p>
        </div>
      </div>
    </div>
  </div>
</section>



</template>

<script setup>

</script>

<style scoped>
/* =========================
   TOP BANNER
========================= */
.about-page {
  padding: 40px 0;
    line-height: 1.7;

}

.about-banner {
  background: #5fa974;
  padding: 28px;
  border-radius: 16px;
  height: 200px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.about-banner h2 {
  font-size: 28px;
  margin-bottom: 8px;
  color: var(--text);
}

.about-banner p {
  color: #fff;
  text-align: center;
  max-width: 700px;
}

/* =========================
   ABOUT SECTION
========================= */
.about-section {
  padding: 0 78px;
}

.about-layout {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 64px;
  align-items: center;
}

.about-image {
  display: flex;
  justify-content: center;
}

/* =========================
   COMMON TEXT
========================= */
.section-title {
  font-size: 38px;
  font-weight: 700;
  margin-bottom: 12px;
}

.section-desc {
  font-size: 16px;
  line-height: 1.7;
  margin-bottom: 24px;
}

/* =========================
   IMAGE
========================= */
.image-ring {
  width: 100%;
  max-width: 450px;
  babout-radius: 18px;
}

.image-ring img {
  width: 100%;
  height: auto;
  object-fit: cover;
}

/* =========================
   RESPONSIVE
========================= */
@media (max-width: 1024px) {
  .about-layout {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .section-title {
    font-size: 32px;
  }
}

@media (max-width: 768px) {
  .about-section {
    padding: 0 20px;
  }

  .section-title {
    font-size: 28px;
  }

  .section-desc {
    font-size: 15px;
  }
}

@media (max-width: 480px) {
  .section-title {
    font-size: 24px;
  }
}
/* =========================
   WHAT WE SERVE
========================= */
.serve-section {
  padding: 50px 0;
  text-align: center;
  line-height: 1.7;
}

.section-serve {
  font-size: 19px;
  /* font-weight: bold!important; */
  color: var(--accent);
  display: block;
  margin-bottom: 6px;
}

.section-heading {
  font-size: 34px;
  font-weight: 700;
  margin-bottom: 48px;
}

.serve-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 40px;
}

.serve-card img {
  height: 200px;
  margin-bottom: 18px;
}

.serve-card h4 {
  font-size: 20px;
  margin-bottom: 8px;
}

.serve-card p {
  font-size: 16px;
  color: #555;
  max-width: 260px;
  margin: auto;
}

/* =========================
   TEAM SECTION (FIGMA MATCH)
========================= */
.team-section {
  padding: 40px 0;
  line-height: 1.7;
    margin-bottom: 20px;

}

.team-wrapper {
  background: #eef5ef;
  border-radius: 32px;
  padding: 50px 60px 80px;
}

/* HEADER ROW */
.team-header-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  align-items: center;
  margin-bottom: 60px;
}

.team-label {
  font-size: 16px;
  font-weight: 600;
  color: var(--accent);
  letter-spacing: 0.5px;
}

.team-title {
  font-size: 36px;
  font-weight: 800;
  margin-top: 6px;
}

.team-header-desc {
  font-size: 16px;
  color: #555;
  max-width: 420px;
  justify-self: end;
}

/* GRID */
.team-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 60px;
  align-items: end;
}

/* MEMBER */
.team-member {
  position: relative;
  text-align: center;
}

/* IMAGE FLOATING */
.team-member img {
  width: 220px;
  height: auto;
  margin-bottom: -10px;
  z-index: 2;
  position: relative;
}

/* GREEN CARD */
.member-card {
  background: #5fa974;
  color: #fff;
  padding: 18px 14px 28px;
  border-radius: 24px;
  min-height: 80px;
}

.member-card h4 {
  font-size: 18px;
  font-weight: 700;
  margin-bottom: 4px;
}

.member-card span {
  font-size: 14px;
  font-weight: 600;
  opacity: 0.9;
  display: block;
  margin-bottom: 10px;
}

.member-card p {
  font-size: 14px;
  font-weight: 500;
  line-height: 1.6;
  opacity: 0.95;
  color:var(--text);
}

/* =========================
   RESPONSIVE
========================= */
@media (max-width: 1024px) {
  .team-header-row {
    grid-template-columns: 1fr;
    text-align: center;
    gap: 16px;
  }

  .team-header-desc {
    justify-self: center;
  }

  .team-grid {
    grid-template-columns: 1fr;
    gap: 80px;
  }

  .team-member img {
    width: 200px;
  }
}

@media (max-width: 600px) {
  .team-wrapper {
    padding: 40px 24px 60px;
  }

  .team-title {
    font-size: 28px;
  }
}


/* =========================
   RESPONSIVE
========================= */
@media (max-width: 1024px) {
  .serve-grid{
    grid-template-columns: 1fr;
    gap: 32px;
  }

  .section-heading {
    font-size: 28px;
  }
}

</style>
