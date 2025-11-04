<template>
  <section class="activities" id="activities">
    <!-- Torn paper top -->
    <div class="torn-paper"></div>

    <!-- Header -->
    <div class="content" data-aos="fade-up">
      <h2 class="title">ACTIVITIES</h2>
      <p class="subtitle">
        Explore exciting adventures and experiences tailored for every traveler.
      </p>
    </div>

    <!-- Cards -->
    <div class="cards-container">
      <div
        v-for="(activity, index) in activities"
        :key="index"
        class="activity-card"
        :data-aos="'zoom-in'"
        :data-aos-delay="index * 100"
        @click="toggleActivity(index)">
        <div class="icon">
          <component :is="activity.icon" />
        </div>
        <h3>{{ activity.title }}</h3>
        <p>{{ activity.description }}</p>

        <!-- Expanded content -->
        <transition name="fade-slide">
          <div v-if="activity.showDetails" class="details-card">
            <img :src="activity.image" alt="activity" />
            <p>
              Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed vitae
              nisi eget justo feugiat sodales. Nulla facilisi. Donec ac magna
              urna. Nam vel efficitur lectus.
            </p>
          </div>
        </transition>
      </div>
    </div>
  </section>
</template>

<script>
import { Mountain, Umbrella, Camera, Bike, Compass } from "lucide-vue-next";
import AOS from "aos";
import "aos/dist/aos.css";

export default {
  name: "TheActivities",
  components: { Mountain, Umbrella, Camera, Bike, Compass },
  data() {
    return {
      activities: [
        {
          title: "Mountain Hiking",
          description: "Experience breathtaking views and nature trails.",
          icon: "Mountain",
          image:
            "https://images.unsplash.com/photo-1554629947-334ff61d85dc?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&q=80&w=436",
          showDetails: false,
        },
        {
          title: "Beach Relaxation",
          description: "Enjoy sunny beaches and crystal-clear waters.",
          icon: "Umbrella",
          image:
            "https://images.unsplash.com/photo-1507525428034-b723cf961d3e?w=800&q=80",
          showDetails: false,
        },
        {
          title: "City Exploration",
          description: "Discover landmarks, cafes, and local culture.",
          icon: "Camera",
          image:
            "https://images.unsplash.com/photo-1498036882173-b41c28a8ba34?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&q=80&w=464",
          showDetails: false,
        },
        {
          title: "Cycling Tours",
          description: "Ride through scenic routes and countryside paths.",
          icon: "Bike",
          image:
            "https://images.unsplash.com/photo-1504274066651-8d31a536b11a?w=800&q=80",
          showDetails: false,
        },
        {
          title: "Adventure Trek",
          description: "Challenge yourself with guided outdoor adventures.",
          icon: "Compass",
          image:
            "https://images.unsplash.com/photo-1533636721434-0e2d61030955?w=800&q=80",
          showDetails: false,
        },
      ],
    };
  },
  methods: {
    toggleActivity(index) {
      this.activities[index].showDetails = !this.activities[index].showDetails;
    },
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
.activities {
  position: relative;
  background: var(--primary-color);
  color: white;
  text-align: center;
  overflow: hidden;
  padding: 120px 20px;
  z-index: 1;
}

.torn-paper {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100px;
  background: var(--gray-bg);
  clip-path: polygon(
    0% 60%,
    10% 65%,
    20% 55%,
    30% 70%,
    40% 60%,
    50% 75%,
    60% 60%,
    70% 70%,
    80% 58%,
    90% 68%,
    100% 60%,
    100% 0,
    0% 0
  );
  z-index: 2;
}

.content {
  margin-bottom: 60px;
  position: relative;
  z-index: 3;
}

.title {
  font-size: 100px;
  font-weight: 800;
  text-transform: uppercase;
  background-image: url("https://images.unsplash.com/photo-1649960861744-d18e65345eaf?ixlib=rb-4.1.0&auto=format&fit=crop&w=1000&q=80");
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
  -webkit-text-fill-color: transparent;
  background-size: cover;
  background-position: center;
  margin-bottom: 20px;
  letter-spacing: 2px;
}

.subtitle {
  color: rgba(255, 255, 255, 0.9);
  font-size: 18px;
  max-width: 700px;
  margin: 0 auto;
  line-height: 1.6;
}

.cards-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
  gap: 30px;
  margin-top: 40px;
  position: relative;
  z-index: 3;
}

.activity-card {
  background: var(--white);
  border-radius: 16px;
  padding: 30px 20px;
  color: var(--text-dark);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  cursor: pointer;
  position: relative;
}

.activity-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 12px 25px rgba(0, 0, 0, 0.2);
  background: var(--secondary-color);
  color: white;
}

.icon {
  width: 70px;
  height: 70px;
  margin: 0 auto 20px;
  background: var(--primary-color);
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
}

.activity-card:hover .icon {
  background: white;
  color: var(--secondary-color);
  transform: rotate(360deg) scale(1.1);
}

.details-card {
  background: var(--white);
  color: var(--text-dark);
  border-radius: 12px;
  padding: 15px;
  margin-top: 20px;
  box-shadow: 0 6px 15px rgba(0, 0, 0, 0.1);
  animation: expand 0.4s ease;
}

.details-card img {
  width: 100%;
  height: 160px;
  object-fit: cover;
  border-radius: 10px;
  margin-bottom: 10px;
}

.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: all 0.4s ease;
}

.fade-slide-enter-from,
.fade-slide-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

@keyframes expand {
  from {
    opacity: 0;
    transform: scaleY(0.9);
  }
  to {
    opacity: 1;
    transform: scaleY(1);
  }
}

@media (max-width: 768px) {
  .title {
    font-size: 40px;
  }
  .subtitle {
    font-size: 16px;
  }
}
</style>
