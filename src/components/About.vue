<template>
  <section id="about" class="about">
    <div class="overlay"></div>
    <div class="container">
      <div class="section-header" data-aos="fade-up">
        <h2>About DemoTrendK</h2>
        <p class="intro">
          We are passionate about creating unforgettable travel experiences.
          With over 15 years of expertise in the travel industry, we specialize
          in crafting personalized journeys to the world's most iconic
          destinations. Our mission is to make your dream vacation a reality
          with exceptional service and unbeatable value.
        </p>
      </div>

      <div class="features-grid">
        <div
          v-for="(feature, index) in features"
          :key="feature.id"
          class="feature-card"
          :data-aos="'zoom-in'"
          :data-aos-delay="index * 100">
          <div class="icon-wrapper">
            <component :is="feature.icon" class="icon" />
          </div>
          <h3>{{ feature.title }}</h3>
          <p>{{ feature.description }}</p>
        </div>
      </div>

      <div class="stats-grid">
        <div
          v-for="(stat, index) in stats"
          :key="stat.id"
          class="stat-card"
          :data-aos="'fade-up'"
          :data-aos-delay="index * 150">
          <div class="stat-number">{{ stat.number }}</div>
          <div class="stat-label">{{ stat.label }}</div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { Globe2, Award, Users, Heart } from "lucide-vue-next";
import AOS from "aos";
import "aos/dist/aos.css";

export default {
  name: "AboutComp",
  components: {
    Globe2,
    Award,
    Users,
    Heart,
  },
  data() {
    return {
      features: [
        {
          id: 1,
          title: "Global Destinations",
          description:
            "Access to over 100+ destinations worldwide with carefully curated itineraries",
          icon: "Globe2",
        },
        {
          id: 2,
          title: "Award Winning",
          description:
            "Recognized as one of the best travel agencies with 5-star customer reviews",
          icon: "Award",
        },
        {
          id: 3,
          title: "Expert Guides",
          description:
            "Professional tour guides with local expertise and cultural knowledge",
          icon: "Users",
        },
        {
          id: 4,
          title: "Best Experience",
          description:
            "Memorable experiences crafted with attention to every detail",
          icon: "Heart",
        },
      ],
      stats: [
        { id: 1, number: "15+", label: "Years Experience" },
        { id: 2, number: "50K+", label: "Happy Travelers" },
        { id: 3, number: "100+", label: "Destinations" },
        { id: 4, number: "98%", label: "Satisfaction Rate" },
      ],
    };
  },
  mounted() {
    AOS.init({
      duration: 1000,
      once: true,
      easing: "ease-out-cubic",
    });
  },
};
</script>

<style scoped>
.about {
  padding: 100px 25px;
  background: var(--gray-bg);
  position: relative;
}

.overlay {
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(255, 255, 255, 0.85);
  z-index: 0;
}

.container {
  position: relative;
  z-index: 1;
}

.section-header {
  text-align: center;
  max-width: 800px;
  margin: 0px auto 50px auto;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 40px;
}

.feature-card {
  position: relative;
  text-align: center;
  background: white;
  border-radius: 16px;
  padding: 30px 20px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  transition: all 0.4s ease;
  overflow: hidden;
  cursor: pointer;
}

.feature-card:hover {
  transform: translateY(-6px) scale(1.05);
  box-shadow: 0 8px 25px var(--secondary-color);
}

.feature-card::before {
  content: "";
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    120deg,
    transparent,
    var(--secondary-color),
    transparent
  );
  transition: all 0.4s ease;
  opacity: 0.3;
}

.feature-card:hover::before {
  left: 100%;
}

.icon-wrapper {
  width: 90px;
  height: 90px;
  margin: 20px auto;
  background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.4s ease;
  z-index: 1;
  position: relative;
}

.icon {
  width: 42px;
  height: 42px;
  color: var(--primary-color);
  transition: transform 0.4s ease, color 0.4s ease;
}

.feature-card:hover .icon-wrapper {
  background: linear-gradient(135deg, #64b5f6 0%, #2196f3 100%);
  box-shadow: 0 8px 20px var(--secondary-color);
}

.feature-card:hover .icon {
  color: white;
  transform: rotate(360deg) scale(1.1);
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 40px;
  padding: 60px 0 20px;
}

.stat-card {
  text-align: center;
  background: white;
  border-radius: 12px;
  padding: 20px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
  transition: all 0.4s ease;
  cursor: pointer;
  position: relative;
  overflow: hidden;
}

.stat-card:hover {
  transform: translateY(-6px) scale(1.05);
  box-shadow: 0 8px 25px var(--secondary-color);
}

.stat-card::before {
  content: "";
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    120deg,
    transparent,
    var(--secondary-color),
    transparent
  );
  transition: all 0.6s ease;
  opacity: 0.3;
}

.stat-card:hover::before {
  left: 100%;
}

.stat-number {
  font-size: 48px;
  font-weight: 700;
  color: var(--primary-color);
  margin-bottom: 8px;
  transition: color 0.3s ease;
}

.stat-card:hover .stat-number {
  color: var(--secondary-color);
}

.stat-label {
  font-size: 16px;
  color: var(--text-light);
}

@media (max-width: 768px) {
  .features-grid,
  .stats-grid {
    grid-template-columns: 1fr;
  }
}
</style>
