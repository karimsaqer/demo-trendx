<template>
  <section class="travel-video-section" data-aos="fade-up">
    <div class="container">
      <div class="text-side" data-aos="fade-right">
        <h1 class="headline">
          Great Opportunity For <br />
          <span class="highlight">Adventure & Travels</span>
        </h1>
        <p class="subtitle">
          Discover new places, cultures, and experiences. Start your journey
          today and create memories that last a lifetime.
        </p>
        <button class="hero-btn">Explore Now</button>
      </div>

      <div class="video-side" data-aos="zoom-in">
        <div class="video-container">
          <!-- Thumbnail -->
          <div v-if="!isPlaying" class="video-preview" @click="playVideo">
            <img
              src="https://images.unsplash.com/photo-1649960861744-d18e65345eaf?ixlib=rb-4.1.0&auto=format&fit=crop&q=80&w=800"
              alt="Travel Preview"
              class="preview-img" />
            <div class="play-btn">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="60"
                height="60"
                viewBox="0 0 16 16">
                <circle
                  cx="8"
                  cy="8"
                  r="7"
                  stroke="#fff"
                  stroke-width="2"
                  fill="rgba(0,0,0,0.3)" />
                <polygon points="6,4.5 12,8 6,11.5" fill="#fff" />
              </svg>
            </div>
          </div>

          <!-- Video -->
          <iframe
            v-else
            class="video-frame"
            :src="videoUrl"
            frameborder="0"
            allow="autoplay; fullscreen"
            allowfullscreen></iframe>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import AOS from "aos";
import "aos/dist/aos.css";

export default {
  name: "TravelVideoPreview",
  data() {
    return {
      isPlaying: false,
      videoUrl: "",
    };
  },
  methods: {
    playVideo() {
      this.isPlaying = true;
      this.videoUrl =
        "https://www.youtube.com/embed/n9LgeoJE4EI?autoplay=1&mute=1";
    },
  },
  mounted() {
    AOS.init({ duration: 1000, once: true });
  },
};
</script>

<style scoped>
.travel-video-section {
  padding: 100px 40px;
  background: var(--gray-bg);
  display: flex;
  align-items: center;
  justify-content: center;
}

.container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 60px;
  max-width: 1200px;
}

/* === TEXT SIDE === */
.text-side {
  flex: 1;
  min-width: 300px;
}

.headline {
  font-size: 2.5rem;
  font-weight: 700;
  color: var(--text-dark);
  line-height: 1.3;
}

.highlight {
  color: var(--secondary-color, #feaf0c);
  font-style: italic;
}

.subtitle {
  color: var(--text-dark);
  font-size: 1.1rem;
  margin: 20px 0 30px;
  max-width: 500px;
}

.hero-btn {
  background: var(--primary-color);
  color: var(--white);
  border: none;
  border-radius: 50px;
  padding: 12px 30px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
}
.hero-btn:hover {
  transform: scale(1.05);
}

/* === VIDEO SIDE === */
.video-side {
  flex: 1;
  display: flex;
  justify-content: center;
  position: relative;
}

.video-container {
  width: 100%;
  max-width: 500px;
  aspect-ratio: 16/9;
  border-radius: 20px;
  overflow: hidden;
  position: relative;
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.25);
}

.video-preview {
  width: 100%;
  height: 100%;
  position: relative;
  cursor: pointer;
  overflow: hidden;
}

.preview-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.4s ease;
}

.video-preview:hover .preview-img {
  transform: scale(1.05);
}

.play-btn {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: radial-gradient(circle, #42a5f5, #1e88e5);
  width: 90px;
  height: 90px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
  transition: transform 0.3s ease;
}

.video-preview:hover .play-btn {
  transform: translate(-50%, -50%) scale(1.1);
}

.video-frame {
  width: 100%;
  height: 100%;
  border: none;
}

/* === RESPONSIVE === */
@media (max-width: 992px) {
  .container {
    flex-direction: column;
    text-align: center;
  }
  .text-side {
    order: 2;
  }
  .video-side {
    order: 1;
  }
  .headline {
    font-size: 2rem;
  }
}
</style>
