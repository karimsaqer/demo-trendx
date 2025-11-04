<template>
  <section id="trips" class="travel-offers">
    <div class="container">
      <div class="section-header">
        <h2>Our Best Travel Packages</h2>
        <p>
          Discover amazing destinations with exclusive discounts and
          unforgettable experiences
        </p>
      </div>

      <div class="filter-buttons">
        <button
          v-for="place in places"
          :key="place"
          :class="{ active: selectedPlace === place }"
          @click="changeFilter(place)">
          {{ place }}
        </button>
      </div>

      <transition-group name="offer" tag="div" class="offers-grid" appear>
        <div v-for="offer in filteredOffers" :key="offer.id" class="offer-card">
          <div class="offer-image">
            <img :src="offer.image" :alt="offer.title" />
            <span class="discount-badge">{{ offer.discount }}</span>
          </div>
          <div class="offer-content">
            <h3>{{ offer.title }}</h3>
            <div class="location">
              <svg
                width="16"
                height="16"
                fill="currentColor"
                viewBox="0 0 16 16">
                <path
                  d="M8 16s6-5.686 6-10A6 6 0 0 0 2 6c0 4.314 6 10 6 10zm0-7a3 3 0 1 1 0-6 3 3 0 0 1 0 6z" />
              </svg>
              <span>{{ offer.location }}</span>
            </div>
            <p class="description">{{ offer.description }}</p>

            <div class="offer-details">
              <div class="detail">
                <svg
                  width="16"
                  height="16"
                  fill="currentColor"
                  viewBox="0 0 16 16">
                  <path
                    d="M11 6.5a.5.5 0 0 1 .5-.5h1a.5.5 0 0 1 .5.5v1a.5.5 0 0 1-.5.5h-1a.5.5 0 0 1-.5-.5v-1z" />
                  <path
                    d="M3.5 0a.5.5 0 0 1 .5.5V1h8V.5a.5.5 0 0 1 1 0V1h1a2 2 0 0 1 2 2v11a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2V3a2 2 0 0 1 2-2h1V.5a.5.5 0 0 1 .5-.5zM1 4v10a1 1 0 0 0 1 1h12a1 1 0 0 0 1-1V4H1z" />
                </svg>
                <span>{{ offer.duration }}</span>
              </div>
              <div class="detail">
                <svg
                  width="16"
                  height="16"
                  fill="currentColor"
                  viewBox="0 0 16 16">
                  <path
                    d="M7 14s-1 0-1-1 1-4 5-4 5 3 5 4-1 1-1 1H7zm4-6a3 3 0 1 0 0-6 3 3 0 0 0 0 6z" />
                  <path
                    fill-rule="evenodd"
                    d="M5.216 14A2.238 2.238 0 0 1 5 13c0-1.355.68-2.75 1.936-3.72A6.325 6.325 0 0 0 5 9c-4 0-5 3-5 4s1 1 1 1h4.216z" />
                  <path d="M4.5 8a2.5 2.5 0 1 0 0-5 2.5 2.5 0 0 0 0 5z" />
                </svg>
                <span>{{ offer.people }}</span>
              </div>
            </div>

            <div class="offer-footer">
              <div class="price">
                <span class="from">From</span>
                <span class="old-price">${{ offer.oldPrice }}</span>
                <span class="new-price">${{ offer.newPrice }}</span>
              </div>
              <button class="book-btn">Book Now</button>
            </div>
          </div>
        </div>
      </transition-group>
    </div>
  </section>
</template>

<script>
import AOS from "aos";

export default {
  name: "TravelOffers",
  data() {
    return {
      selectedPlace: "All",
      places: ["All", "Disney", "Istanbul", "London"],
      offers: [
        // Disney
        {
          id: 1,
          title: "Disneyland Family Fun",
          location: "Disneyland, California",
          description:
            "Experience magical adventures with your family at the happiest place on Earth.",
          duration: "5 Days",
          people: "2 Adults + 2 Kids",
          oldPrice: 1999,
          newPrice: 1499,
          discount: "25% OFF",
          category: "Disney",
          image:
            "https://images.unsplash.com/photo-1605443791607-80a259dd3c3c?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&q=80&w=387",
        },
        {
          id: 2,
          title: "Disney Escape",
          location: "Disneyland, California",
          description:
            "A romantic getaway with fireworks and luxury Disney hotel stay.",
          duration: "4 Days",
          people: "2 Adults",
          oldPrice: 1599,
          newPrice: 1199,
          discount: "30% OFF",
          category: "Disney",
          image:
            "https://images.unsplash.com/photo-1545580492-8859ba8323f0?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&q=80&w=774",
        },
        {
          id: 3,
          title: "Disney Adventure Package",
          location: "Disneyland, California",
          description:
            "Thrilling rides, meet Disney heroes, and get exclusive backstage tours.",
          duration: "6 Days",
          people: "3 Adults",
          oldPrice: 2199,
          newPrice: 1699,
          discount: "22% OFF",
          category: "Disney",
          image:
            "https://plus.unsplash.com/premium_photo-1708391920708-a94e998c209d?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&q=80&w=387",
        },

        // Istanbul
        {
          id: 4,
          title: "Istanbul Historical Tour",
          location: "Istanbul, Turkey",
          description:
            "Discover ancient mosques, bazaars, and palaces on this guided journey.",
          duration: "5 Days",
          people: "2 Adults",
          oldPrice: 1299,
          newPrice: 999,
          discount: "23% OFF",
          category: "Istanbul",
          image:
            "https://plus.unsplash.com/premium_photo-1691338312403-e9f7f7984eeb?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&q=80&w=464",
        },
        {
          id: 5,
          title: "Istanbul City Lights Cruise",
          location: "Istanbul, Turkey",
          description:
            "Enjoy a romantic night cruise on the Bosphorus with music and dinner.",
          duration: "3 Days",
          people: "2 Adults",
          oldPrice: 899,
          newPrice: 699,
          discount: "20% OFF",
          category: "Istanbul",
          image:
            "https://images.unsplash.com/photo-1524231757912-21f4fe3a7200?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&q=80&w=871",
        },
        {
          id: 6,
          title: "Istanbul Local Experience",
          location: "Istanbul, Turkey",
          description:
            "Taste local food, shop at hidden bazaars, and explore authentic districts.",
          duration: "7 Days",
          people: "4 Adults",
          oldPrice: 1699,
          newPrice: 1299,
          discount: "24% OFF",
          category: "Istanbul",
          image:
            "https://images.unsplash.com/photo-1527838832700-5059252407fa?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&q=80&w=398",
        },

        // London
        {
          id: 7,
          title: "London Sightseeing Tour",
          location: "London, UK",
          description:
            "Visit Big Ben, Buckingham Palace, and the London Eye with our guide.",
          duration: "4 Days",
          people: "2 Adults",
          oldPrice: 1799,
          newPrice: 1399,
          discount: "22% OFF",
          category: "London",
          image:
            "https://images.unsplash.com/photo-1513635269975-59663e0ac1ad?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&q=80&w=870",
        },
        {
          id: 8,
          title: "London Royal Experience",
          location: "London, UK",
          description:
            "Exclusive access to royal landmarks and afternoon tea at famous cafés.",
          duration: "5 Days",
          people: "2 Adults + 1 Child",
          oldPrice: 1999,
          newPrice: 1599,
          discount: "20% OFF",
          category: "London",
          image:
            "https://images.unsplash.com/photo-1505761671935-60b3a7427bad?w=800",
        },
        {
          id: 9,
          title: "London Art & Culture Walk",
          location: "London, UK",
          description:
            "Explore art galleries, museums, and street performances across the city.",
          duration: "6 Days",
          people: "2 Adults",
          oldPrice: 1699,
          newPrice: 1299,
          discount: "24% OFF",
          category: "London",
          image:
            "https://images.unsplash.com/photo-1528909514045-2fa4ac7a08ba?w=800",
        },
      ],
    };
  },
  computed: {
    filteredOffers() {
      if (this.selectedPlace === "All") return this.offers;
      return this.offers.filter((o) => o.category === this.selectedPlace);
    },
  },
  methods: {
    changeFilter(place) {
      this.selectedPlace = "";
      this.$nextTick(() => {
        this.selectedPlace = place;
      });
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
.travel-offers {
  padding: 80px 0;
  background: url("https://images.unsplash.com/photo-1488646953014-85cb44e25828?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&q=80&w=735")
    no-repeat center center / cover;
  background-attachment: fixed;
  position: relative;
}

.travel-offers::before {
  content: "";
  position: absolute;
  inset: 0;
  background: rgba(0, 0, 0, 0.75);
  z-index: 0;
}

.travel-offers > .container {
  position: relative;
  z-index: 1;
}

.filter-buttons {
  display: flex;
  gap: 10px;
  justify-content: center;
  align-items: center;
  margin: 18px 0 28px;
  flex-wrap: wrap;
}

.filter-buttons button {
  background: var(--white);
  border: 2px solid rgba(0, 0, 0, 0.06);
  color: var(--text-dark);
  padding: 10px 18px;
  border-radius: 999px;
  font-weight: 700;
  letter-spacing: 0.2px;
  cursor: pointer;
  transition: all 220ms ease;
  box-shadow: 0 6px 18px rgba(17, 24, 39, 0.03);
}

.filter-buttons button:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 30px rgba(17, 24, 39, 0.06);
}

.filter-buttons button.active {
  background-color: var(--primary-color);
  color: #fff;
  border: none;
  transform: translateY(-6px) scale(1.03);
  box-shadow: 0 18px 40px rgba(0, 0, 0, 0.12);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.section-header {
  text-align: center;
  margin-bottom: 60px;
}

.section-header h2 {
  font-size: 36px;
  color: var(--primary-color);
  margin-bottom: 12px;
}

.section-header p {
  font-size: 16px;
  color: var(--secondary-color);
}

.offers-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 30px;
}

.offer-card {
  background: var(--white);
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s, box-shadow 0.3s;
}

.offer-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

.offer-image {
  position: relative;
  height: 250px;
  overflow: hidden;
}

.offer-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.discount-badge {
  position: absolute;
  top: 16px;
  right: 16px;
  background: var(--secondary-color);
  color: var(--text-dark);
  padding: 8px 16px;
  border-radius: 20px;
  font-weight: 700;
  font-size: 14px;
}

.offer-content {
  padding: 24px;
}

.offer-content h3 {
  font-size: 22px;
  color: var(--text-dark);
  margin-bottom: 8px;
}

.location {
  display: flex;
  align-items: center;
  gap: 6px;
  color: var(--text-light);
  font-size: 14px;
  margin-bottom: 12px;
}

.description {
  color: var(--text-light);
  font-size: 14px;
  line-height: 1.6;
  margin-bottom: 16px;
}

.offer-details {
  display: flex;
  gap: 20px;
  margin-bottom: 20px;
  padding-bottom: 20px;
  border-bottom: 1px solid #e0e0e0;
}

.detail {
  display: flex;
  align-items: center;
  gap: 6px;
  color: var(--text-light);
  font-size: 14px;
}

.offer-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.price {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.from {
  font-size: 12px;
  color: var(--text-light);
}

.old-price {
  font-size: 14px;
  color: var(--text-light);
  text-decoration: line-through;
}

.new-price {
  font-size: 24px;
  color: var(--primary-color);
  font-weight: 700;
}

.book-btn {
  background: var(--primary-color);
  color: var(--white);
  padding: 12px 28px;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.3s, transform 0.2s;
}

.book-btn:hover {
  background: #2a6d91;
  transform: scale(1.05);
}

@media (max-width: 768px) {
  .offers-grid {
    grid-template-columns: 1fr;
  }
}

.offer-enter-active,
.offer-leave-active {
  transition: all 0.5s ease;
}
.offer-enter-from {
  opacity: 0;
  transform: scale(0.95);
}
.offer-enter-to {
  opacity: 1;
  transform: scale(1);
}
.offer-leave-from {
  opacity: 1;
  transform: scale(1);
}
.offer-leave-to {
  opacity: 0;
  transform: scale(0.95);
}

/* Mounting animation for the section */
.travel-offers {
  animation: fadeInUp 1s ease;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
