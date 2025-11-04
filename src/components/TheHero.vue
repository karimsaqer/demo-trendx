<template>
  <section id="home" class="hero">
    <div class="hero-overlay"></div>
    <div class="hero-content">
      <h1>Discover Your Next Adventure</h1>
      <p>Explore the world's most amazing destinations with exclusive offers</p>
      <button class="cta-btn" @click="scrollToTrips">View Our Trips</button>
    </div>
  </section>
</template>

<script>
export default {
  name: "TheHero",
  methods: {
    scrollToTrips() {
      const element = document.getElementById("trips");
      if (element) {
        element.scrollIntoView({ behavior: "smooth", block: "start" });
      }
    },
  },
};
</script>

<style scoped>
.hero {
  position: relative;
  height: 600px;
  background-image: url("https://images.unsplash.com/photo-1464746133101-a2c3f88e0dd9?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&q=80&w=843");
  background-size: cover;
  background-position: center;
  display: flex;
  align-items: center;
  justify-content: center;
}

.hero-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
}

.hero-content {
  position: relative;
  z-index: 2;
  text-align: center;
  color: var(--white);
  max-width: 800px;
  padding: 0 20px;
}

.hero-content h1 {
  font-size: 48px;
  margin-bottom: 20px;
  font-weight: 700;
}

.hero-content p {
  font-size: 20px;
  margin-bottom: 30px;
  opacity: 0.95;
}

.cta-btn {
  background: var(--secondary-color);
  color: var(--text-dark);
  padding: 16px 40px;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  transition: transform 0.3s, box-shadow 0.3s;
}

.cta-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(254, 175, 12, 0.4);
}

@media (max-width: 768px) {
  .hero {
    height: 500px;
  }

  .hero-content h1 {
    font-size: 32px;
  }

  .hero-content p {
    font-size: 16px;
  }
}
</style>
