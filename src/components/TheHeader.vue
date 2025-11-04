<template>
  <header class="header">
    <div class="container">
      <div class="logo">
        <h2>DemoTrendK</h2>
      </div>

      <nav class="nav">
        <a href="#home" @click.prevent="scrollTo('home')">Home</a>
        <a href="#trips" @click.prevent="scrollTo('trips')">Trips</a>
        <a href="#about" @click.prevent="scrollTo('about')">About Us</a>
        <a href="#contact" @click.prevent="scrollTo('contact')">Contact</a>
      </nav>

      <div class="right-menu">
        <div class="dropdown">
          <div class="menu-item">
            <i class="fa-solid fa-globe"></i>
            <span>English</span>
            <i class="fa-solid fa-chevron-down small"></i>
          </div>
          <ul class="dropdown-menu">
            <li>English</li>
            <li>Arabic</li>
            <li>French</li>
            <li>Spanish</li>
          </ul>
        </div>

        <div class="dropdown">
          <div class="menu-item">
            <span>USD</span>
            <i class="fa-solid fa-chevron-down small"></i>
          </div>
          <ul class="dropdown-menu">
            <li>USD</li>
            <li>EUR</li>
            <li>EGP</li>
            <li>SAR</li>
          </ul>
        </div>

        <div class="menu-item search">
          <i class="fa-solid fa-magnifying-glass"></i>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "TheHeader",
  methods: {
    scrollTo(section) {
      const element = document.getElementById(section);
      if (element) {
        element.scrollIntoView({ behavior: "smooth", block: "start" });
      }
    },
  },
};
</script>

<style scoped>
.header {
  background: var(--white);
  padding: 18px 0;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
  position: sticky;
  top: 0;
  z-index: 1000;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 30px;
}

.logo h2 {
  color: var(--primary-color);
  font-size: 24px;
  font-weight: 700;
  letter-spacing: 1px;
}

.nav {
  display: flex;
  gap: 40px;
}

.nav a {
  color: var(--text-dark);
  text-decoration: none;
  font-size: 16px;
  font-weight: 500;
  transition: color 0.3s;
}

.nav a:hover {
  color: var(--primary-color);
}

.right-menu {
  display: flex;
  align-items: center;
  gap: 25px;
}

.menu-item {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 15px;
  color: var(--text-dark);
  cursor: pointer;
  transition: color 0.3s;
  position: relative;
}

.menu-item:hover {
  color: var(--primary-color);
}

.menu-item i {
  font-size: 16px;
}

.menu-item .small {
  font-size: 10px;
  opacity: 0.7;
}

.dropdown {
  position: relative;
}

.dropdown-menu {
  display: none;
  position: absolute;
  top: 130%;
  left: 0;
  background: var(--white);
  border-radius: 8px;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.1);
  list-style: none;
  padding: 8px 0;
  min-width: 120px;
  animation: fadeIn 0.25s ease;
}

.dropdown-menu li {
  padding: 8px 15px;
  font-size: 14px;
  color: var(--text-dark);
  cursor: pointer;
  transition: background 0.2s, color 0.2s;
}

.dropdown-menu li:hover {
  background: var(--primary-color);
  color: var(--white);
}

.dropdown:hover .dropdown-menu {
  display: block;
}

.menu-item.search i {
  font-size: 18px;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(-5px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 768px) {
  .nav {
    gap: 20px;
  }

  .right-menu {
    display: none;
  }
}
</style>
