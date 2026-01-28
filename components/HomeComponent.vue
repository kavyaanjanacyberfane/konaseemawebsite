<template>

  
  <!-- Categories section -->
  <section id="doctors" class="doctors-section">
    <div class="container">
      <div class="doctors-header">
        <h3 class="section-subtitle">EXPLORE OUR CATEGORIES</h3>
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
        </div>
      </div>
    </div>
  </section>

  <!-- Testimonial section -->
  <section class="testimonial-section">
    <div class="container testimonial-layout">
      <!-- LEFT CONTENT -->
      <div class="testimonial-content">
        <h3 class="section-subtitle">WHAT THEY SAY</h3>
        <h1 class="section-title">What Our Customers Say About Us!</h1>

        <p class="section-desc">
          “Fudo is the best. Besides the many and delicious meals, the service
          is also very good, especially in the very fast delivey. I highly
          recommend Fudo to you”.
        </p>

        <!-- RIGHT COLUMN : REVIEWS -->
        <div class="testimonial-right">
          <div class="review-card">
            <img src="/images/swetha.jpg" alt="user" class="review-avatar" />
            <div class="review-info">
              <span class="review-name">Deepika Choudary</span>
              <div>
              <span class="review-role">Food Enthusiast</span>

              </div>
              <div class="stars">★★★★★ <span>4.8</span></div>
            </div>
          </div>

          <span class="our-review" style="font-weight: 500;text-align: start;">Our Reviews</span>

          <div class="review-users">
            <img src="/images/swetha.jpg" alt="user" />
            <img src="/images/swetha.jpg" alt="user" />
            <img src="/images/swetha.jpg" alt="user" />
            <div class="more-users">+12</div>
          </div>
        </div>
      </div>

      <!-- RIGHT IMAGE -->
      <div class="testimonial-image">
        <div class="image-ring">
          <NuxtImg src="/images/chef.png" alt="Chef" format="webp" />
        </div>
      </div>
    </div>
  </section>

  <!-- Download app section -->
  <section class="app-section">
    <div class="container app-layout">
      <div class="app-image">
        <div class="image-ring">
          <NuxtImg src="/images/appimg.png" alt="App" format="webp" />
        </div>
      </div>

      <div class="app-content">
        <h3 class="section-subtitle">DOWNLOAD APP</h3>
        <h1 class="section-title">Get Started With Konaseema App Today</h1>

        <p class="section-desc">
          Discover food wherever and whenever and get your food delivered
          quickly.
        </p>

        <button class="btn-primary">Get The App</button>
      </div>
    </div>
  </section>
</template>

<script setup>
const doctors = [
  { id: 1, name: "Soup", image: "/images/soup.png" },
  { id: 2, name: "Starter", image: "/images/soup.png" },
  { id: 3, name: "Biryani", image: "/images/soup.png" },
  { id: 4, name: "Pulao", image: "/images/soup.png" },
  { id: 5, name: "Noodles", image: "/images/soup.png" },
  { id: 6, name: "Fried Rice", image: "/images/soup.png" },
  { id: 7, name: "Mocktails", image: "/images/soup.png" },
  { id: 8, name: "Curries", image: "/images/soup.png" },
];
</script>

<style scoped>

/* =========================
   COMMON
========================= */
.section-title {
  font-size: 38px;
  font-weight: 700;
  margin-bottom: 8px;
}

.section-subtitle {
  font-size: 20px;
  color: #159038;
  margin-bottom: 20px;
}

.section-desc {
  font-size: 16px;
  line-height: 1.7;
  margin-bottom: 28px;
}

.image-ring {
  width: 100%;
  max-width: 500px;
}

.image-ring img {
  width: 100%;
  height: auto;
  object-fit: contain;
}

/* =========================
   TESTIMONIAL SECTION
========================= */
.testimonial-section {
  padding: 60px 78px;
  overflow-x: hidden;
}

.testimonial-layout {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 64px;
  align-items: center;
}

.testimonial-image {
  display: flex;
  justify-content: center;
}

.testimonial-right {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

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

.review-name{
  font-weight: 600;
}

.review-role {
  font-size: 12px;
  padding-top: 15px;
  color: lightslategray;
}

.stars {
  color: #f5b400;
  font-size: 14px;
}

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
  margin-left: -14px;
}

.more-users {
  background: #159038;
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 13px;
  font-weight: 600;
}

/* =========================
   DOCTORS / CATEGORIES
========================= */
.doctors-section {
  padding: 40px 40px 0;
}

.doctors-header {
  text-align: center;
  margin-bottom: 48px;
}

.doctors-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 24px;
}

.doctor-card {
  text-align: center;
}

.doctor-image {
  width: 200px;
  height: 200px;
  object-fit: cover;
  border-radius: 16px;
  border: 1px solid #e5e5e5;
}

.doctor-card h3 {
  margin-top: 12px;
  font-size: 18px;
  color: #0e7b2d;
}

/* =========================
   APP SECTION
========================= */
.app-section {
  margin: 78px;
  padding: 32px;
  background: #89bd9780;
  border-radius: 20px;
}

.app-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 64px;
  align-items: center;
}

/* =========================
   RESPONSIVE BREAKPOINTS
========================= */

/* Tablets */
@media (max-width: 1024px) {
  .testimonial-layout,
  .app-layout {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .testimonial-image,
  .app-image {
    order: -1;
  }

  .section-title {
    font-size: 32px;
  }
}

/* Mobile */
@media (max-width: 768px) {
  .testimonial-section{
    padding: 0 20px;
  }

  .app-section {
    margin: 40px 20px;
    padding: 24px;
  }

  .section-title {
    font-size: 28px;
  }

  .section-desc {
    font-size: 15px;
  }

  .doctor-image {
    width: 180px;
    height: 180px;
  }
}

/* Small mobile */
@media (max-width: 480px) {
  .section-title {
    font-size: 24px;
  }


  .review-card {
    flex-direction: column;
    text-align: center;
  }

  .review-users {
    justify-content: center;
  }
  .our-review{
    text-align: center!important;

  }
}
/* =========================
   RESPONSIVE
========================= */
@media (max-width: 900px) {
  .doctors-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media (max-width: 700px) {
  .doctors-grid {
gap:20px;  }
}
@media (max-width: 675px) {
  /* .doctors-grid {
    grid-template-columns: repeat(2, 1fr);

    }  */
    .doctor-image {
  width: 150px;
  height: 150px;
    }
   }


@media (max-width: 521px) {
  .doctors-grid {
 gap:10px;  }

}

@media (max-width: 596px) {
  .doctors-grid {
    grid-template-columns: repeat(2, 1fr);
    } 
        .doctor-image {
  width: 180px;
  height: 180px;
    }
    
  }
@media (max-width: 500px) {
  .doctors-grid {
    grid-template-columns: repeat(2, 1fr);
    } 
        .doctor-image {
  width: 150px;
  height: 150px;
    }
    
  }

  @media (max-width: 450px) {
        .doctor-image {
  width: 130px;
  height: 130px;
    }
    
  }

  @media (max-width: 380px) {
  .doctors-grid {
    grid-template-columns: 1fr;
    } 
            .doctor-image {
  width: 200px;
  height: 200px;
    }
  }
</style>