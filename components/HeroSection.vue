<script setup>
// (No special logic required here for now.)
// If you need to pass props (e.g. dynamic text or links), you can add them via defineProps().
</script>

<template>
  <section
    class="hero-section"
    aria-label="Főoldal hőskép: profi bontás és földmunka Keszthelyen"
  >
    <div class="hero-section__overlay">
      <div class="hero-section__content">
        <!-- Main headline (SEO: H1) -->
        <h1 class="hero-section__title">
          Professzionális bontás és földmunka Keszthely szívében –<br />
          <span class="hero-section__subtitle"
            >több mint 25 éve az Ön szolgálatában.</span
          >
        </h1>

        <!-- Call‐to‐action button -->
        <!-- TODO: Replace `#` with your real route, e.g. `/contact` or a NuxtLink if you have a contact page/component. -->
        <a
          href="#"
          class="hero-section__button"
          role="button"
          aria-label="Árajánlat kérése"
        >
          Árajánlat kérése
        </a>
      </div>
    </div>

    <!-- Contact info bar at bottom of hero -->
    <address class="contact-bar">
      <div class="contact-bar__item">
        <!-- Location icon (inline SVG) -->
        <svg
          class="contact-bar__icon"
          xmlns="http://www.w3.org/2000/svg"
          width="16"
          height="16"
          viewBox="0 0 24 24"
          fill="currentColor"
          aria-hidden="true"
        >
          <path
            d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38
                 0-2.5-1.12-2.5-2.5s1.12-2.5
                 2.5-2.5 2.5 1.12 2.5 2.5-1.12
                 2.5-2.5 2.5z"
          />
        </svg>
        <span class="contact-bar__text">8360 Keszthely, Gyópi út 13.</span>
      </div>

      <div class="contact-bar__item">
        <!-- Email icon (inline SVG) -->
        <svg
          class="contact-bar__icon"
          xmlns="http://www.w3.org/2000/svg"
          width="16"
          height="16"
          viewBox="0 0 24 24"
          fill="currentColor"
          aria-hidden="true"
        >
          <path
            d="M20 4H4c-1.1 0-2 .9-2 2v12c0 1.1.9
                 2 2 2h16c1.1 0 2-.9
                 2-2V6c0-1.1-.9-2-2-2zm0
                 4l-8 5-8-5V6l8 5 8-5v2z"
          />
        </svg>
        <a class="contact-bar__text" href="mailto:szilveszter0827@gmail.com"
          >szilveszter0827@gmail.com</a
        >
      </div>

      <div class="contact-bar__item">
        <!-- Phone icon (inline SVG) -->
        <svg
          class="contact-bar__icon"
          xmlns="http://www.w3.org/2000/svg"
          width="16"
          height="16"
          viewBox="0 0 24 24"
          fill="currentColor"
          aria-hidden="true"
        >
          <path
            d="M6.62 10.79a15.466 15.466
                 0 006.59 6.59l2.2-2.2c.27-.27.67-.36
                 1.02-.24 1.12.37 2.33.57 3.57.57.55
                 0 1 .45 1 1V20c0 .55-.45 1-1
                 1C10.07 21 3 13.93 3
                 5c0-.55.45-1 1-1h3.5c.55
                 0 1 .45 1 1 0 1.24.20 2.45.57
                 3.57.11.35.03.74-.25
                 1.02l-2.2 2.2z"
          />
        </svg>
        <a class="contact-bar__text" href="tel:+36203444017">06 20 344 40 17</a>
      </div>
    </address>
  </section>
</template>

<style lang="scss" scoped>
/*───────────────────────────────────────────────────────────
    1. ROOT / BLOCK: .hero-section
  ───────────────────────────────────────────────────────────*/
.hero-section {
  position: relative;
  width: 100%;
  height: 100vh; /* fullscreen hero */
  background-image: url('/img/test.jpg'); /* <-- adjust path */
  background-size: cover;
  background-position: center center;
  background-repeat: no-repeat;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  color: #ffffff; /* white text */
  font-family: 'Helvetica Neue', Arial, sans-serif; /* adjust to your project’s font */
}

/* A dark overlay to ensure text legibility on any part of background */
.hero-section__overlay {
  position: absolute;
  inset: 0; /* full coverage */
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 1;
}

/* Container for centering content horizontally & vertically (slightly top) */
.hero-section__content {
  position: relative;
  z-index: 2;
  max-width: 1200px;
  margin: 0 auto;
  padding-top: 15vh; /* push down a bit */
  padding-left: 1rem;
  padding-right: 1rem;
  text-align: left;
}

/*───────────────────────────────────────────────────────────
    2. ELEMENTS INSIDE .hero-section
  ───────────────────────────────────────────────────────────*/
.hero-section__title {
  font-size: 2.5rem;
  line-height: 1.2;
  font-weight: 700;
  margin: 0;
}

.hero-section__subtitle {
  display: block; /* forces subtitle on new line */
  font-size: 1.5rem;
  font-weight: 400;
  margin-top: 0.5rem;
}

/* Call‐to‐action button */
.hero-section__button {
  display: inline-block;
  margin-top: 2rem;
  padding: 0.75rem 1.5rem;
  background-color: #ff6600; /* orange, adjust to your brand color */
  color: #ffffff;
  font-size: 1rem;
  font-weight: 600;
  text-decoration: none;
  border-radius: 4px;
  transition: background-color 0.2s ease;
}

.hero-section__button:hover,
.hero-section__button:focus {
  background-color: #e65c00; /* -10% sötétebb narancs */
  outline: none;
}

/*───────────────────────────────────────────────────────────
    3. CONTACT BAR (BLOCK: .contact-bar)
  ───────────────────────────────────────────────────────────*/
.contact-bar {
  position: relative;
  z-index: 2;
  width: 100%;
  background-color: #ffdd00; /* bright yellow */
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0.75rem 1rem;
  font-size: 0.9rem;
  color: #000000;
}

/* Each item (address / email / phone) is flexed */
.contact-bar__item {
  display: flex;
  align-items: center;
  margin: 0 1.5rem;
}

/* Icon next to text */
.contact-bar__icon {
  flex-shrink: 0;
  width: 1rem;
  height: 1rem;
  margin-right: 0.5rem;
  color: inherit; /* inherit text color (black) */
}

.contact-bar__text {
  color: inherit;
  text-decoration: none;
}

/* On very narrow screens, stack contact items vertically */
@media (max-width: 600px) {
  .contact-bar {
    flex-direction: column;
    text-align: center;
  }
  .contact-bar__item {
    margin: 0.5rem 0;
  }
}
</style>
