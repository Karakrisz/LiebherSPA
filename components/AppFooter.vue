<script setup>
import { ref, reactive } from 'vue'

const form = reactive({
  name: '',
  phone: '',
  email: '',
  subject: '',
  message: '',
})

const isSubmitting = ref(false)
const submitMessage = ref('')

const onSubmit = async (event) => {
  event.preventDefault()

  if (isSubmitting.value) return

  isSubmitting.value = true
  submitMessage.value = ''

  try {
    const webhookUrl = 'https://services.leadconnectorhq.com/hooks/H88YJRj6KegTU4bp21tx/webhook-trigger/b2ceebf4-0303-4a29-b26b-10caa6f0f151'

    const payload = {
      name: form.name,
      phone: form.phone,
      email: form.email,
      subject: form.subject,
      message: form.message,
      source: 'Kontakt űrlap (Footer)',
      form_type: 'general_contact',
      submission_date: new Date().toISOString(),
    }

    const response = await fetch(webhookUrl, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify(payload),
    })

    if (response.ok) {
      submitMessage.value = '✅ Köszönjük a megkeresést! Hamarosan jelentkezünk.'

      // Form resetelése
      form.name = ''
      form.phone = ''
      form.email = ''
      form.subject = ''
      form.message = ''

      // Üzenet eltüntetése 5 mp után
      setTimeout(() => {
        submitMessage.value = ''
      }, 5000)
    } else {
      throw new Error('Hiba a küldéskor')
    }
  } catch (error) {
    console.error('Form submission error:', error)
    submitMessage.value = '❌ Hiba történt. Kérjük próbálja újra, vagy hívjon minket!'
  } finally {
    isSubmitting.value = false
  }
}
</script>

<template>
  <footer>
    <section class="contact" aria-labelledby="contact-heading">
      <div class="container">
        <div class="contact__container">
          <!-- BAL OLDAL: ŰRLAP -->
          <div class="contact__form-wrapper">
            <h2 id="contact-heading" class="contact__heading">Kapcsolat</h2>
            <form class="contact__form" @submit="onSubmit">
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
                    :disabled="isSubmitting"
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
                    :disabled="isSubmitting"
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
                    :disabled="isSubmitting"
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
                    :disabled="isSubmitting"
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
                    :disabled="isSubmitting"
                  ></textarea>
                </div>
              </div>

              <p class="contact__disclaimer">
                A küldés gombra kattintva automatikusan elfogadja az
                <NuxtLink
                  to="/adatvedelmi-tajekoztato"
                  target="_blank"
                  rel="noopener noreferrer"
                  class="contact__disclaimer-link"
                >
                  Adatkezelési Nyilatkozatot
                </NuxtLink>
                .
              </p>

              <button type="submit" class="contact__submit" :disabled="isSubmitting">
                {{ isSubmitting ? 'Küldés...' : 'Küldés' }}
              </button>

              <!-- Success/Error Message -->
              <div
                v-if="submitMessage"
                class="submit-message"
                :class="{
                  success: submitMessage.includes('✅'),
                  error: submitMessage.includes('❌'),
                }"
              >
                {{ submitMessage }}
              </div>
            </form>
          </div>

          <!-- JOBB OLDAL: Kontakt-infó -->
          <div class="contact__info-wrapper">
            <ul class="contact__info-list">
              <li class="contact__info-item">
                <span class="contact__info-icon" aria-hidden="true">
                  <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none">
                    <path d="M12 12.75C13.6569 12.75 15 11.4069 15 9.75C15 8.09315 13.6569 6.75 12 6.75C10.3431 6.75 9 8.09315 9 9.75C9 11.4069 10.3431 12.75 12 12.75Z" stroke="#FAFAFA" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M19.5 9.75C19.5 16.5 12 21.75 12 21.75C12 21.75 4.5 16.5 4.5 9.75C4.5 7.76088 5.29018 5.85322 6.6967 4.4467C8.10322 3.04018 10.0109 2.25 12 2.25C13.9891 2.25 15.8968 3.04018 17.3033 4.4467C18.7098 5.85322 19.5 7.76088 19.5 9.75Z" stroke="#FAFAFA" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                </span>
                <div>
                  <span class="contact__info-label">Cím</span>
                  <span class="contact__info-text">8360 Keszthely, Gyöpi út 13.</span>
                </div>
              </li>
              <li class="contact__info-item">
                <span class="contact__info-icon" aria-hidden="true">
                  <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none">
                    <path d="M21 5.25L12 13.5L3 5.25" stroke="#FAFAFA" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M3 5.25H21V18C21 18.1989 20.921 18.3897 20.7803 18.5303C20.6397 18.671 20.4489 18.75 20.25 18.75H3.75C3.55109 18.75 3.36032 18.671 3.21967 18.5303C3.07902 18.3897 3 18.1989 3 18V5.25Z" stroke="#FAFAFA" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M10.3639 12L3.23145 18.5381" stroke="#FAFAFA" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M20.7685 18.5381L13.636 12" stroke="#FAFAFA" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                </span>
                <div>
                  <span class="contact__info-label">E-mail cím</span>
                  <span class="contact__info-text">szilveszter0827@gmail.com</span>
                </div>
              </li>
              <li class="contact__info-item">
                <span class="contact__info-icon" aria-hidden="true">
                  <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none">
                    <path d="M15.4116 13.6257C15.5154 13.5566 15.6349 13.5145 15.7591 13.5032C15.8834 13.4919 16.0085 13.5118 16.1231 13.561L20.5444 15.542C20.6934 15.6057 20.8177 15.7159 20.8989 15.8562C20.98 15.9964 21.0135 16.1592 20.9944 16.3201C20.8487 17.4086 20.3127 18.4071 19.486 19.13C18.6593 19.8529 17.5982 20.2509 16.5 20.2501C13.1185 20.2501 9.87548 18.9068 7.48439 16.5157C5.0933 14.1246 3.75 10.8816 3.75 7.5001C3.74916 6.40192 4.1472 5.3408 4.87009 4.5141C5.59298 3.6874 6.59152 3.15138 7.68 3.00573C7.84091 2.98661 8.00368 3.02012 8.14395 3.10124C8.28422 3.18236 8.39444 3.30673 8.45813 3.45573L10.4391 7.88073C10.4877 7.99438 10.5076 8.1183 10.4968 8.24146C10.486 8.36463 10.4449 8.48321 10.3772 8.58666L8.37375 10.9689C8.30269 11.0761 8.26066 11.1999 8.25179 11.3283C8.24291 11.4566 8.26749 11.585 8.32313 11.701C9.09844 13.2882 10.7391 14.9092 12.3309 15.677C12.4475 15.7324 12.5766 15.7564 12.7053 15.7467C12.834 15.737 12.958 15.6939 13.065 15.6217L15.4116 13.6257Z" stroke="#FAFAFA" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                </span>
                <div>
                  <span class="contact__info-label">Telefonszám</span>
                  <span class="contact__info-text">06 20 344 40 17</span>
                </div>
              </li>
            </ul>
          </div>
        </div>

        <!-- LÁBRÉSZ -->
        <div class="footer">
          <div class="footer__company">Liebher & Liebher Bt</div>
          <nav class="footer__nav">
            <ul class="footer__nav-list">
              <li class="footer__nav-item">
                <NuxtLink to="/rolunk" class="footer__nav-link">Rólunk</NuxtLink>
              </li>
              <li class="footer__nav-item">
                <NuxtLink to="/szolgaltatasok" class="footer__nav-link">Szolgáltatásaink</NuxtLink>
              </li>
              <!-- <li class="footer__nav-item">
                <NuxtLink to="/galeria" class="footer__nav-link">Galéria</NuxtLink>
              </li> -->
              <li class="footer__nav-item">
                <NuxtLink to="/kapcsolat" class="footer__nav-link">Kapcsolat</NuxtLink>
              </li>
              <li class="footer__nav-item">
                <NuxtLink to="/adatvedelmi-tajekoztato" class="footer__nav-link">Adatkezelési Nyilatkozat</NuxtLink>
              </li>
            </ul>
          </nav>
        </div>
      </div>
    </section>
  </footer>
</template>


<style lang="scss" scoped>
.container {
  max-width: 1200px;
  margin: 0 auto;
}

.contact {
  padding: 5em 2em 0 2em;

  &__container {
    display: flex;
    flex-direction: column;
    background-color: #111111;
    border-radius: 1rem;
    overflow: hidden;

    @media (min-width: 768px) {
      flex-direction: row;
    }
  }

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
    z-index: 10;

    &::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: -0.4em;
      width: 6em;
      height: 0.5em;
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
    font-family: inherit;
    transition: box-shadow 0.2s ease;

    &:focus {
      outline: none;
      box-shadow: 0 0 0 2px rgba(255, 106, 0, 0.7);
    }

    &:disabled {
      background-color: #f8f9fa;
      opacity: 0.6;
      cursor: not-allowed;
    }
  }

  &__textarea {
    min-height: 8rem;
  }

  &__disclaimer {
    font-size: 0.85rem;
    color: #cccccc;
    margin: 0;
    line-height: 1.4;

    a {
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

    &:hover:not(:disabled),
    &:focus:not(:disabled) {
      background-color: #e65c00;
      outline: none;
    }

    &:disabled {
      opacity: 0.6;
      cursor: not-allowed;
    }
  }

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

.submit-message {
  padding: 15px;
  border-radius: 8px;
  margin-top: 1rem;
  font-weight: bold;
  text-align: center;

  &.success {
    background-color: #d4edda;
    color: #155724;
    border: 1px solid #c3e6cb;
  }

  &.error {
    background-color: #f8d7da;
    color: #721c24;
    border: 1px solid #f5c6cb;
  }
}

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
}
</style>