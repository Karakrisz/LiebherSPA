<template>
  <footer>
    <section class="contact" aria-labelledby="contact-heading">
      <!-- Itt jön az új container-wrapper -->
      <div class="container">
        <div class="contact__container">
          <!-- BAL OLDAL: ŰRLAP -->
          <div class="contact__form-wrapper">
            <h2 id="contact-heading" class="contact__heading">Kapcsolat</h2>
            <form class="contact__form" @submit.prevent="onSubmit">
              <div class="contact__form-row">
                <div class="contact__field">
                  <label for="name" class="contact__label">Név*</label>
                  <input
                    id="name"
                    v-model="form.name"
                    type="text"
                    required
                    placeholder="Név"
                    class="contact__input"
                  />
                </div>
                <div class="contact__field">
                  <label for="phone" class="contact__label">Telefonszám*</label>
                  <input
                    id="phone"
                    v-model="form.phone"
                    type="tel"
                    required
                    placeholder="Telefonszám"
                    class="contact__input"
                  />
                </div>
              </div>

              <div class="contact__form-row">
                <div class="contact__field">
                  <label for="email" class="contact__label">E-mail cím*</label>
                  <input
                    id="email"
                    v-model="form.email"
                    type="email"
                    required
                    placeholder="E-mail cím"
                    class="contact__input"
                  />
                </div>
                <div class="contact__field">
                  <label for="subject" class="contact__label">Tárgy</label>
                  <input
                    id="subject"
                    v-model="form.subject"
                    type="text"
                    placeholder="Tárgy"
                    class="contact__input"
                  />
                </div>
              </div>

              <div class="contact__form-row">
                <div class="contact__field contact__field--full">
                  <label for="message" class="contact__label">Üzenet</label>
                  <textarea
                    id="message"
                    v-model="form.message"
                    rows="6"
                    placeholder="Üzenet"
                    class="contact__textarea"
                  ></textarea>
                </div>
              </div>

              <p class="contact__disclaimer">
                A küldés gombra kattintva automatikusan elfogadja az
                <NuxtLink
                  to="/"
                  target="_blank"
                  rel="noopener noreferrer"
                  class="contact__disclaimer-link"
                >
                  Adatkezelési Nyilatkozatot </NuxtLink
                >.
              </p>

              <button type="submit" class="contact__submit">Küldés</button>
            </form>
          </div>

          <!-- JOBB OLDAL: Kontakt‐infó -->
          <div class="contact__info-wrapper">
            <ul class="contact__info-list">
              <li class="contact__info-item">
                <span class="contact__info-icon" aria-hidden="true">📍</span>
                <div>
                  <span class="contact__info-label">Cím</span>
                  <span class="contact__info-text"
                    >8360 Keszthely, Gyöpi út 13.</span
                  >
                </div>
              </li>
              <li class="contact__info-item">
                <span class="contact__info-icon" aria-hidden="true">✉️</span>
                <div>
                  <span class="contact__info-label">E-mail cím</span>
                  <span class="contact__info-text">
                    szilveszter0827@gmail.com
                  </span>
                </div>
              </li>
              <li class="contact__info-item">
                <span class="contact__info-icon" aria-hidden="true">📞</span>
                <div>
                  <span class="contact__info-label">Telefonszám</span>
                  <span class="contact__info-text">06 20 344 40 17</span>
                </div>
              </li>
            </ul>
          </div>
        </div>

        <!-- LÁBRÉSZ: Cég neve és navigáció -->
        <div class="footer">
          <div class="footer__company">Liebher & Liebher Bt</div>
          <nav class="footer__nav">
            <ul class="footer__nav-list">
              <li class="footer__nav-item">
                <NuxtLink to="/" class="footer__nav-link">Rólunk</NuxtLink>
              </li>
              <li class="footer__nav-item">
                <NuxtLink to="/" class="footer__nav-link"
                  >Szolgáltatásaink</NuxtLink
                >
              </li>
              <li class="footer__nav-item">
                <NuxtLink to="/" class="footer__nav-link">Galéria</NuxtLink>
              </li>
              <li class="footer__nav-item">
                <NuxtLink to="/" class="footer__nav-link">Kapcsolat</NuxtLink>
              </li>
              <li class="footer__nav-item">
                <NuxtLink to="/" class="footer__nav-link"
                  >Ajánlatkérés</NuxtLink
                >
              </li>
              <li class="footer__nav-item">
                <NuxtLink to="/" class="footer__nav-link"
                  >Adatkezelési Nyilatkozat</NuxtLink
                >
              </li>
            </ul>
          </nav>
        </div>
        <div class="footer__credits">
          <a
            href="https://digitalseedstudio.com"
            target="_blank"
            rel="noopener noreferrer"
            class="footer__credits-link"
          >
            <img alt="Digital Seed Studio" class="footer__credits-logo" />
          </a>
        </div>
      </div>
    </section>
  </footer>
</template>

<script setup>
import { reactive } from 'vue'

const form = reactive({
  name: '',
  phone: '',
  email: '',
  subject: '',
  message: '',
})

const onSubmit = () => {
  // Itt lehet AJAX‐hívást lebonyolítani, pl.:
  // await $fetch('/api/contact', { method: 'POST', body: form })
  console.log('Űrlap elküldve:', { ...form })
  alert('Köszönjük a megkeresést! Hamarosan jelentkezünk.')
  form.name = ''
  form.phone = ''
  form.email = ''
  form.subject = ''
  form.message = ''
}
</script>

<style lang="scss" scoped>
.container {
  max-width: 1200px;
  margin: 0 auto;
}

.contact {
  &__container {
    display: flex;
    flex-direction: column;
    background-color: #111111;
    border-radius: 1rem;
    overflow: hidden;
  }

  @media (min-width: 768px) {
    &__container {
      flex-direction: row;
      height: 100%;
    }
  }

  /* ================================================
     BAL OLDAL: ŰRLAP
     ================================================ */
  &__form-wrapper {
    background-color: #111111;
    color: #ffffff;
    padding: 2rem 1rem;

    @media (min-width: 768px) {
      flex: 2 1 60%;
      padding: 3rem 2rem;
    }
  }

  &__heading {
    font-size: 2rem;
    font-weight: 700;
    position: relative;
    display: inline-block;
    margin-bottom: 2rem;

    &::after {
      content: '';
      position: absolute;
      bottom: -0.5rem;
      left: 0;
      width: 100%;
      height: 0.5rem;
      background-color: #ff6a00;
      z-index: -1;
    }
  }

  &__form {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
  }

  &__form-row {
    display: flex;
    flex-direction: column;
    gap: 1rem;

    @media (min-width: 768px) {
      flex-direction: row;
      gap: 1.5rem;
    }
  }

  &__field {
    display: flex;
    flex-direction: column;
    width: 100%;

    &--full {
      width: 100%;
    }
  }

  &__label {
    font-size: 0.9rem;
    margin-bottom: 0.5rem;
    color: #e0e0e0;
  }

  &__input,
  &__textarea {
    background-color: #ffffff;
    border: none;
    border-radius: 0.375rem;
    padding: 0.75rem 1rem;
    font-size: 1rem;
    color: #333333;
    resize: vertical;
    min-height: 2.5rem;
  }

  &__input:focus,
  &__textarea:focus {
    outline: none;
    box-shadow: 0 0 0 2px rgba(255, 106, 0, 0.7);
  }

  &__textarea {
    min-height: 8rem;
  }

  &__disclaimer {
    font-size: 0.85rem;
    color: #cccccc;
    margin: 0;
    line-height: 1.4;

    a.contact__disclaimer-link {
      color: #ffffff;
      text-decoration: underline;
      transition: opacity 0.2s ease;

      &:hover,
      &:focus {
        opacity: 0.8;
        outline: none;
      }
    }
  }

  &__submit {
    margin-top: 1rem;
    align-self: flex-start;
    background-color: #ff6a00;
    color: #ffffff;
    border: none;
    border-radius: 0.375rem;
    padding: 0.75rem 1.5rem;
    font-size: 1rem;
    font-weight: 500;
    cursor: pointer;
    transition: background-color 0.2s ease;

    &:hover,
    &:focus {
      background-color: #e65c00; /* manuálisan számolt, 10%-kal sötétebb */
      outline: none;
    }
  }

  /* ================================================
     JOBB OLDAL: Kontakt‐infó
     ================================================ */
  &__info-wrapper {
    background-color: #ff6a00;
    color: #ffffff;
    padding: 2rem 1.5rem;
    display: flex;
    align-items: center;
    justify-content: center;

    @media (min-width: 768px) {
      flex: 1 1 40%;
      padding: 3rem 2rem;
    }
  }

  &__info-list {
    list-style: none;
    padding: 0;
    margin: 0;
    width: 100%;
    display: flex;
    flex-direction: column;
    gap: 2rem;
  }

  &__info-item {
    display: flex;
    align-items: flex-start;
    gap: 1rem;
  }

  &__info-icon {
    font-size: 1.5rem;
    line-height: 1;
    margin-top: 0.25rem;
  }

  &__info-label {
    display: block;
    font-size: 1rem;
    font-weight: 600;
    margin-bottom: 0.25rem;
  }

  &__info-text {
    font-size: 0.95rem;
    line-height: 1.4;
  }
}

/* ================================================
   LÁBRÉSZ STÍLUSOK
   ================================================ */
.footer {
  background-color: #e6e6e6;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 90%;
  margin: auto;
  border-bottom-left-radius: 1em;
  border-bottom-right-radius: 1em;

  @media (min-width: 768px) {
    flex-direction: row;
    justify-content: space-between;
    padding: 1.5em 2em;
  }

  &__company {
    font-weight: 600;
    font-size: 1.2rem;
    color: #333;
    margin-bottom: 1rem;

    @media (min-width: 768px) {
      margin-bottom: 0;
    }
  }

  &__nav {
    margin-bottom: 1rem;

    @media (min-width: 768px) {
      margin-bottom: 0;
    }
  }

  &__nav-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 1rem;
    list-style: none;
    padding: 0;
    margin: 0;
  }

  &__nav-item {
    font-size: 0.9rem;
  }

  &__nav-link {
    color: #333;
    text-decoration: none;
    transition: color 0.2s ease;

    &:hover,
    &:focus {
      color: #ff6a00;
      outline: none;
    }
  }

  &__credits {
    text-align: center;
    margin: 3em 0;
  }

  &__credits-link {
    display: block;
    transition: opacity 0.2s ease;

    &:hover,
    &:focus {
      opacity: 0.8;
      outline: none;
    }
  }

  &__credits-logo {
    height: 2rem;
    width: auto;
  }
}
</style>
