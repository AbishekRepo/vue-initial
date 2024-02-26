<template>
  <nav class="navbar" :class="{ 'dark-mode': isDarkMode }">
    <a href="#" class="logo">Logo</a>
    <ul class="navbar-nav">
      <li
        v-for="(page, index) in pages"
        :key="index"
        @click="setActiveIndex(index)"
      >
        <a href="#" class="nav-link"></a>{{ page.link.text }}
      </li>
    </ul>
    <div class="dark-mode-toggle">
      <div class="toggle-switch" @click="toggleDarkMode()">
        {{ isDarkMode ? "Light" : "Dark" }}
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  props: ["pages", "setActiveIndex"],
  data() {
    return {
      isDarkMode: false,
    };
  },
  methods: {
    toggleDarkMode() {
      this.isDarkMode = !this.isDarkMode;
    },
  },
};
</script>

<style>
/* Navbar container */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 20px;
  background-color: #f8f9fa;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  position: sticky;
}

/* Logo */
.logo {
  font-size: 1.5rem;
  font-weight: bold;
  text-decoration: none;
  color: #333;
}

/* Navbar links */
.navbar-nav {
  display: flex;
  list-style-type: none;
  margin-right: auto; /* Move the Home links to the right */
  align-items: center;
  gap: 15px;
  cursor: pointer;
}

.navbar-nav li {
  margin-right: 10px;
}

.nav-link {
  text-decoration: none;
  color: #333;
}

/* Dark mode toggle */
.dark-mode-toggle {
  cursor: pointer;
}

.toggle-switch {
  display: inline-block;
  padding: 5px 10px;
  background-color: #333;
  color: #fff;
  border-radius: 20px;
}

/* Dark mode */
.dark-mode {
  background-color: #333;
  color: #fff;
}

.dark-mode .nav-link {
  color: #fff;
}

.dark-mode .logo {
  color: #fff;
}

.dark-mode .toggle-switch {
  background-color: #fff;
  color: #333;
}
</style>
