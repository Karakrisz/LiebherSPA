<template>
  <section
    class="hero-section"
    aria-label="Főoldal hőskép: profi bontás és földmunka Keszthelyen"
  >
    <!-- Félátlátszó overlay, ami az egész hero fölé kerül -->
    <div class="hero-section__overlay"></div>

    <!-- A “fő rész”: itt helyezkedik el a tartalom, középre zárva a contact-bar fölötti területen -->
    <div class="hero-section__main">
      <div class="hero-section__content">
        <h1 class="hero-section__title">
          Professzionális bontás és földmunka Keszthely szívében –<br />
          <span class="hero-section__subtitle"
            >több mint 25 éve az Ön szolgálatában.</span
          >
        </h1>

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

    <!-- Contact-bar fix pozícióban, a hero alján -->
    <address class="contact-bar">
      <div class="contact-bar__item">
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

<script setup>
// Jelenleg nem kell extra logika. Ha NuxtLinket használsz a gombhoz,
// cseréld le a <a href="#">-t <NuxtLink to="/contact">–re.
</script>

<style lang="scss" scoped>
/*───────────────────────────────────────────────────────────
    1. .hero-section: full-height, flex‐oszlop, hogy a contact-bar
       mindig alul legyen, a fő rész pedig középre igazolt legyen
  ───────────────────────────────────────────────────────────*/
.hero-section {
  position: relative;
  width: 100%;
  height: 100vh;
  background-image: url('/img/test.jpg'); /* beállítod a saját képed útját */
  background-size: cover;
  background-position: center center;
  background-repeat: no-repeat;
  display: flex;
  flex-direction: column;
  /* Így a .hero-section__main (fő rész) kitölti a rendelkezésre álló magasságot
       a contact-bar aljáig, majd a contact-bar fixen lent marad. */
  @media screen and (max-width: 767px) {
    padding: 2em;
  }
}

/* Az overlay marad teljesen lefedő: a hero-section szülőn belül */
.hero-section__overlay {
  position: absolute;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.8);
  z-index: 1;
}

/*───────────────────────────────────────────────────────────
    2. .hero-section__main: ez a hero "fő" része a contact-bar
       fölött. Itt van a flex középre/ középen igazítva a content.
  ───────────────────────────────────────────────────────────*/
.hero-section__main {
  position: relative;
  z-index: 2;

  /* Kitölti a maradék magasságot a contact-bar-ig */
  flex: 1;

  /* Flex középre mindkét tengelyen */
  display: flex;
  align-items: center; /* vízszintes középre */
}

/*───────────────────────────────────────────────────────────
    3. .hero-section__content: maga a tartalom (szöveg+gomb)
  ───────────────────────────────────────────────────────────*/
.hero-section__content {
  max-width: 1200px; /* igény szerint tetszőleges érték */
  margin: auto;
  color: #ffffff;
}

/* Fejléc (h1) és alcím */
.hero-section__title {
  font-size: 2.5rem;
  line-height: 1.2;
  font-weight: 700;
  margin: 0;
  width: 60%;
}

.hero-section__subtitle {
  display: block;
  font-size: 1.5rem;
  font-weight: 400;
  margin-top: 0.5rem;
  color: #ffffff;
}

/* CTA gomb */
.hero-section__button {
  display: inline-block;
  margin-top: 2rem;
  padding: 0.75rem 1.5rem;
  background-color: #ff6d00;
  color: #ffffff;
  font-size: 1rem;
  font-weight: 600;
  text-decoration: none;
  border-radius: 4px;
  transition: background-color 0.2s ease;
}

.hero-section__button:hover,
.hero-section__button:focus {
  background-color: #e65c00; /* manuálisan sötétebb árnyalat */
  outline: none;
}

/*───────────────────────────────────────────────────────────
    4. contact-bar: fixen a hero alján, sárga háttérrel
  ───────────────────────────────────────────────────────────*/
.contact-bar {
  position: relative;
  z-index: 2;
  width: 100%;
  background-color: #ffd51e;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1em;
  font-size: 0.9rem;
  color: #000000;
  /* Mivel a szülő .hero-section display:flex és flex-direction:column,
       a contact-bar a .hero-section__main után kerül a végére. */
}

/* contact-bar belső elemei */
.contact-bar__item {
  display: flex;
  align-items: center;
  margin: 0 1.5rem;
}

.contact-bar__icon {
  flex-shrink: 0;
  width: 1rem;
  height: 1rem;
  margin-right: 0.5rem;
  color: inherit;
}

.contact-bar__text {
  color: inherit;
  text-decoration: none;
  font-style: normal;
}

/* Mobilon a kontakt-elemek egymás alá kerülnek */
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
