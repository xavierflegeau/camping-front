<template>
  <div class="hero">
    <header class="header">
      <!-- Logo -->
      <div class="logo">
        <img src="/images/favicon.ico" alt="logo" />
      </div>

      <!-- RIGHT SECTION -->
      <div class="right-section">
        <!-- Social -->
        <div class="social">
          <!-- Instagram -->
          <a href="#" aria-label="Instagram">
            <svg class="icon" viewBox="0 0 24 24">
              <path
                fill="currentColor"
                d="M7 2C4.2 2 2 4.2 2 7v10c0 2.8 2.2 5 5 5h10c2.8 0
                5-2.2 5-5V7c0-2.8-2.2-5-5-5H7zm10
                2c1.7 0 3 1.3 3 3v10c0 1.7-1.3
                3-3 3H7c-1.7 0-3-1.3-3-3V7c0-1.7
                1.3-3 3-3h10zm-5 3a5 5 0 100
                10 5 5 0 000-10zm0 2a3 3 0 110
                6 3 3 0 010-6zm4.8-.9a1.1
                1.1 0 100 2.2 1.1 1.1 0 000-2.2z"
              />
            </svg>
          </a>

          <!-- Facebook -->
          <a href="#" aria-label="Facebook">
            <svg class="icon" viewBox="0 0 24 24">
              <path
                fill="currentColor"
                d="M13 22v-8h3l1-4h-4V7c0-1
                .3-2 2-2h2V1h-3c-3 0-5 2-5
                5v3H6v4h3v8h4z"
              />
            </svg>
          </a>
        </div>

        <!-- Phone -->
        <a class="phone" href="tel:+33981926786"> 09 81 92 67 86 </a>
        <!-- Contact -->
        <a class="contact"> Contact </a>
      </div>
    </header>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped>
.hero {
  background-size: cover;
  background-position: center;
  height: 120px;
}

/* HEADER */

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 40px;
  background: transparent;
  color: white;
}

/* LOGO */

.logo img {
  height: 50px;
}

/* RIGHT SIDE */

.right-section {
  display: flex;
  align-items: center;
  gap: 20px;
}

/* SOCIAL */

.social {
  display: flex;
  gap: 12px;
}

.icon {
  width: 22px;
  height: 22px;
  color: white;
  cursor: pointer;
}

/* PHONE */

.phone {
  background: var(--primary-color);
  padding: 10px 18px;
  border-radius: 25px;
  font-weight: 600;
  text-decoration: none;
  color: white;
  display: inline-block;
}

/* CONTACT */

.contact {
  cursor: pointer;
}

/* MOBILE */

@media (max-width: 768px) {
  .contact {
    display: none;
  }

  .phone {
    padding: 8px 14px;
    font-size: 14px;
  }
}
</style>
