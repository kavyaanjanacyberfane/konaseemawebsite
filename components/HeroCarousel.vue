<template>
  <section class="hero-section">
    <div class="hero-viewport">
      <div class="container">
        <div
          class="hero-track"
          :style="{
            transform: `translateX(${translateX}px)`,
            '--slide-width': slideWidth + 'px',
          }"
          ref="track"
        >
          <div
            class="hero-slide"
            v-for="(slide, index) in loopedSlides"
            :key="index"
          >
            <!-- LEFT CONTENT -->
            <div class="hero-content">
              <span class="hero-tag">{{ slide.tag }}</span>
              <h1>{{ slide.title }}</h1>
              <p>{{ slide.text }}</p>
              <button class="btn-primary">Order Now</button>
            </div>

            <!-- RIGHT IMAGE -->
            <div class="hero-image">
              <img :src="slide.image" alt="Food Image" />
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- DOTS -->
    <div class="hero-dots">
      <span
        v-for="(_, i) in slides"
        :key="i"
        :class="{ active: current === i }"
        @click="goTo(i)"
      />
    </div>
  </section>
</template>

<script setup>
import { ref, computed, onMounted, onBeforeUnmount } from "vue";

const slides = [
  {
    tag: "Flat Discount",
    title: "Flat 30% Off on All Orders!",
    text: "Enjoy your favorite dishes at unbelievable prices. Limited-time offer on dine-in and takeaway.",
    image: "/images/hero1.png",
  },
  {
    tag: "Special Combo",
    title: "Delicious Meals at Best Prices",
    text: "Taste authentic Andhra flavors crafted with love and tradition.",
    image: "/images/hero1.png",
  },
  {
    tag: "Today’s Special",
    title: "Authentic Andhra Meals",
    text: "Traditional recipes cooked with authentic coastal flavors.",
    image: "/images/hero1.png",
  },
];

// infinite loop
const loopedSlides = [...slides, ...slides, ...slides];

const current = ref(0);
const slideWidth = ref(0);
const gap = 32;
const track = ref(null);
let timer;

const isMobile = () => window.innerWidth < 768;

/* TRANSLATION LOGIC */
const translateX = computed(() => {
  const offset = (current.value + slides.length) * (slideWidth.value + gap);

  // MOBILE → full width slide
  if (isMobile()) {
    return -offset;
  }

  // DESKTOP → centered slide
  const viewportWidth = window.innerWidth;
  const centerOffset = viewportWidth / 2 - slideWidth.value / 2;
  return -offset + centerOffset;
});

/* SLIDE WIDTH LOGIC */
const updateSizes = () => {
  const w = window.innerWidth;

  slideWidth.value = w >= 1200 ? 920 : w >= 992 ? 780 : w >= 768 ? 660 : w - 32; // mobile full width
};

const goTo = (index) => {
  current.value = index;
};

onMounted(() => {
  updateSizes();
  window.addEventListener("resize", updateSizes);

  timer = setInterval(() => {
    current.value = (current.value + 1) % slides.length;
  }, 5000);
});

onBeforeUnmount(() => {
  clearInterval(timer);
  window.removeEventListener("resize", updateSizes);
});
</script>

<style scoped>
/* SECTION */
.hero-section {
  padding: 40px 0;
  overflow: hidden;
}

/* VIEWPORT */
.hero-viewport {
  overflow: hidden;
}

/* TRACK */
.hero-track {
  display: flex;
  gap: 32px;
  transition: transform 0.8s ease;
}

/* SLIDE */
.hero-slide {
  flex: 0 0 auto;
  width: var(--slide-width);
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 48px 56px;
  background: #5fa974;
  border-radius: 28px;
  position: relative;
  overflow: hidden;
}

/* LIGHT SHAPE */
.hero-slide::after {
  content: "";
  position: absolute;
  bottom: -80px;
  left: -80px;
  width: 140%;
  height: 200px;
  background: rgba(255, 255, 255, 0.22);
  transform: rotate(-7deg);
}

/* hero-slide[data-v-1663c05c]::after {
    content: "";
    position: absolute;
    bottom: -110px;
    left: -80px;
    width: 80%;
    height: 200px;
    background: rgba(255, 255, 255, 0.22);
    transform: rotate(-8deg);
    border-radius: 32px;
}
 */

/* CONTENT */
.hero-content {
  max-width: 460px;
  color: #fff;
  z-index: 2;
}

.hero-content h1 {
  font-family: poppins, sans-serif;
}

.hero-tag {
  font-size: 28px;
  font-weight: 800;
  color: #3A3838;
  font-family: poppins, sans-serif;
}

.hero-content h1 {
  font-size: clamp(24px, 4vw, 44px);
  line-height: 1.15;
  margin: 14px 0;
}

.hero-content p {
  font-size: 15px;
  line-height: 1.6;
  margin-bottom: 22px;
}

/* IMAGE */
.hero-image {
  z-index: 2;
}

.hero-image img {
  width: clamp(180px, 22vw, 320px);
  height: clamp(180px, 22vw, 320px);
  border-radius: 50%;
  background: #fff;
  padding: 10px;
  object-fit: cover;
}

/* DOTS */
.hero-dots {
  display: flex;
  justify-content: center;
  gap: 8px;
  margin-top: 18px;
}

.hero-dots span {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #cfe6d6;
  cursor: pointer;
}

.hero-dots span.active {
  background: var(--accent);
}

/* MOBILE */
@media (max-width: 768px) {
  .hero-slide {
    padding: 8px 15px;
    gap: 15px;
    border-radius: 20px;
  }

  .hero-content {
    max-width: 100%;
  }
}
</style>
