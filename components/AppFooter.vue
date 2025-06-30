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
                <span class="contact__info-icon" aria-hidden="true"
                  ><svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="24"
                    height="24"
                    viewBox="0 0 24 24"
                    fill="none"
                  >
                    <path
                      d="M12 12.75C13.6569 12.75 15 11.4069 15 9.75C15 8.09315 13.6569 6.75 12 6.75C10.3431 6.75 9 8.09315 9 9.75C9 11.4069 10.3431 12.75 12 12.75Z"
                      stroke="#FAFAFA"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                    <path
                      d="M19.5 9.75C19.5 16.5 12 21.75 12 21.75C12 21.75 4.5 16.5 4.5 9.75C4.5 7.76088 5.29018 5.85322 6.6967 4.4467C8.10322 3.04018 10.0109 2.25 12 2.25C13.9891 2.25 15.8968 3.04018 17.3033 4.4467C18.7098 5.85322 19.5 7.76088 19.5 9.75Z"
                      stroke="#FAFAFA"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    /></svg
                ></span>
                <div>
                  <span class="contact__info-label">Cím</span>
                  <span class="contact__info-text"
                    >8360 Keszthely, Gyöpi út 13.</span
                  >
                </div>
              </li>
              <li class="contact__info-item">
                <span class="contact__info-icon" aria-hidden="true"
                  ><svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="24"
                    height="24"
                    viewBox="0 0 24 24"
                    fill="none"
                  >
                    <path
                      d="M21 5.25L12 13.5L3 5.25"
                      stroke="#FAFAFA"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                    <path
                      d="M3 5.25H21V18C21 18.1989 20.921 18.3897 20.7803 18.5303C20.6397 18.671 20.4489 18.75 20.25 18.75H3.75C3.55109 18.75 3.36032 18.671 3.21967 18.5303C3.07902 18.3897 3 18.1989 3 18V5.25Z"
                      stroke="#FAFAFA"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                    <path
                      d="M10.3639 12L3.23145 18.5381"
                      stroke="#FAFAFA"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                    <path
                      d="M20.7685 18.5381L13.636 12"
                      stroke="#FAFAFA"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    /></svg
                ></span>
                <div>
                  <span class="contact__info-label">E-mail cím</span>
                  <span class="contact__info-text">
                    szilveszter0827@gmail.com
                  </span>
                </div>
              </li>
              <li class="contact__info-item">
                <span class="contact__info-icon" aria-hidden="true"
                  ><svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="24"
                    height="24"
                    viewBox="0 0 24 24"
                    fill="none"
                  >
                    <path
                      d="M15.4116 13.6257C15.5154 13.5566 15.6349 13.5145 15.7591 13.5032C15.8834 13.4919 16.0085 13.5118 16.1231 13.561L20.5444 15.542C20.6934 15.6057 20.8177 15.7159 20.8989 15.8562C20.98 15.9964 21.0135 16.1592 20.9944 16.3201C20.8487 17.4086 20.3127 18.4071 19.486 19.13C18.6593 19.8529 17.5982 20.2509 16.5 20.2501C13.1185 20.2501 9.87548 18.9068 7.48439 16.5157C5.0933 14.1246 3.75 10.8816 3.75 7.5001C3.74916 6.40192 4.1472 5.3408 4.87009 4.5141C5.59298 3.6874 6.59152 3.15138 7.68 3.00573C7.84091 2.98661 8.00368 3.02012 8.14395 3.10124C8.28422 3.18236 8.39444 3.30673 8.45813 3.45573L10.4391 7.88073C10.4877 7.99438 10.5076 8.1183 10.4968 8.24146C10.486 8.36463 10.4449 8.48321 10.3772 8.58666L8.37375 10.9689C8.30269 11.0761 8.26066 11.1999 8.25179 11.3283C8.24291 11.4566 8.26749 11.585 8.32313 11.701C9.09844 13.2882 10.7391 14.9092 12.3309 15.677C12.4475 15.7324 12.5766 15.7564 12.7053 15.7467C12.834 15.737 12.958 15.6939 13.065 15.6217L15.4116 13.6257Z"
                      stroke="#FAFAFA"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    /></svg
                ></span>
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
                <NuxtLink to="/rolunk" class="footer__nav-link">Rólunk</NuxtLink>
              </li>
              <li class="footer__nav-item">
                <NuxtLink to="/szolgaltatasok" class="footer__nav-link"
                  >Szolgáltatásaink</NuxtLink
                >
              </li>
              <li class="footer__nav-item">
                <NuxtLink to="/galeria" class="footer__nav-link">Galéria</NuxtLink>
              </li>
              <li class="footer__nav-item">
                <NuxtLink to="/kapcsolat" class="footer__nav-link">Kapcsolat</NuxtLink>
              </li>
              <li class="footer__nav-item">
                <NuxtLink to="/kapcsolat" class="footer__nav-link"
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
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="88"
              height="36"
              viewBox="0 0 88 36"
              fill="none"
            >
              <g opacity="0.4" clip-path="url(#clip0_4003_459)">
                <path
                  d="M42.3025 3.79639H45.2191C47.9534 3.79639 49.8903 5.39222 49.8903 7.65112C49.8903 9.91002 47.9534 11.5171 45.2191 11.5171H42.3025V3.79639ZM45.5837 9.53916C46.7686 9.53916 47.6117 8.75247 47.6117 7.65112C47.6117 6.54977 46.7686 5.77433 45.5837 5.77433H44.5127V9.53916H45.5837Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M51.0068 3.79639H53.2171V11.5171H51.0068V3.79639Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M58.2073 6.99939H61.8759V10.281C61.067 11.1463 59.8707 11.652 58.6402 11.652C56.2933 11.652 54.3223 9.82021 54.3223 7.65122C54.3223 5.48222 56.2933 3.66162 58.6402 3.66162C59.8707 3.66162 61.067 4.16734 61.8759 5.02145L60.2467 6.42624C59.8593 5.93176 59.2669 5.63956 58.6402 5.63956C57.5351 5.63956 56.6009 6.5611 56.6009 7.65122C56.6009 8.74133 57.5351 9.67411 58.6402 9.67411C59.0276 9.67411 59.4036 9.56173 59.734 9.35944V8.60647H58.2073V6.99939Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M63.1062 3.79639H65.3165V11.5171H63.1062V3.79639Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M68.6092 5.74061H66.2964V3.79639H73.1322V5.74061H70.8194V11.5171H68.6092V5.74061Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M78.5553 10.4832H75.8323L75.4336 11.5171H72.9385L75.9462 3.79639H78.4413L81.4491 11.5171H78.954L78.5553 10.4832ZM77.9286 8.8761L77.1995 6.9993L76.4589 8.8761H77.9286Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M88.0001 9.57287V11.5171H82.144V3.79639H84.3543V9.57287H88.0001Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M41.71 20.7195L42.9404 19.2698C43.7379 19.8879 44.6038 20.2138 45.5266 20.2138C46.1305 20.2138 46.4495 20.0115 46.4495 19.6743C46.4495 19.3035 46.176 19.2473 45.0937 19C43.3961 18.6179 42.0859 18.1796 42.0859 16.5726C42.0859 14.9655 43.3164 14.0327 45.1734 14.0327C46.5292 14.0327 47.5888 14.3923 48.4547 15.0779L47.3495 16.6175C46.6204 16.1006 45.8229 15.8421 45.1165 15.8421C44.581 15.8421 44.319 16.0556 44.319 16.3478C44.319 16.7411 44.5924 16.8648 45.7089 17.1008C47.5318 17.4829 48.6711 17.9661 48.6711 19.4383C48.6711 21.0679 47.4065 22.0231 45.4469 22.0231C44.0341 22.0231 42.7012 21.5848 41.71 20.7195Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M51.8726 16.1117V16.9771H55.5981V18.9213H51.8726V19.944H55.9627V21.8882H49.6624V14.1675H55.9627V16.1117H51.8726Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M59.2894 16.1117V16.9771H63.0149V18.9213H59.2894V19.944H63.3795V21.8882H57.0791V14.1675H63.3795V16.1117H59.2894Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M64.4961 14.1675H67.4127C70.147 14.1675 72.0839 15.7633 72.0839 18.0222C72.0839 20.2811 70.147 21.8882 67.4127 21.8882H64.4961V14.1675ZM67.7773 19.9102C68.9622 19.9102 69.8053 19.1236 69.8053 18.0222C69.8053 16.9209 68.9622 16.1454 67.7773 16.1454H66.7063V19.9102H67.7773Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M41.71 31.0344L42.9404 29.5847C43.7379 30.2028 44.6038 30.5287 45.5266 30.5287C46.1305 30.5287 46.4495 30.3264 46.4495 29.9893C46.4495 29.6184 46.176 29.5622 45.0937 29.315C43.3961 28.9329 42.0859 28.4946 42.0859 26.8875C42.0859 25.2804 43.3164 24.3477 45.1734 24.3477C46.5292 24.3477 47.5888 24.7073 48.4547 25.3928L47.3495 26.9325C46.6204 26.4155 45.8229 26.157 45.1165 26.157C44.581 26.157 44.319 26.3705 44.319 26.6627C44.319 27.0561 44.5924 27.1797 45.7089 27.4157C47.5318 27.7978 48.6711 28.2811 48.6711 29.7533C48.6711 31.3828 47.4065 32.3381 45.4469 32.3381C44.0341 32.3381 42.7012 31.8998 41.71 31.0344Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M51.5535 26.4266H49.2407V24.4824H56.0766V26.4266H53.7638V32.2031H51.5535V26.4266Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M56.9424 28.7754V24.4824H59.1526V28.6631C59.1526 29.652 59.7793 30.36 60.6679 30.36C61.5566 30.36 62.1832 29.652 62.1832 28.6631V24.4824H64.3934V28.7754C64.3934 30.8658 62.8554 32.338 60.6679 32.338C58.4804 32.338 56.9424 30.8658 56.9424 28.7754Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M65.6809 24.4824H68.5975C71.3319 24.4824 73.2687 26.0783 73.2687 28.3372C73.2687 30.5961 71.3319 32.2031 68.5975 32.2031H65.6809V24.4824ZM68.9621 30.2252C70.147 30.2252 70.9901 29.4385 70.9901 28.3372C70.9901 27.2358 70.147 26.4604 68.9621 26.4604H67.8912V30.2252H68.9621Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M74.3853 24.4824H76.5955V32.2031H74.3853V24.4824Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M77.7007 28.3372C77.7007 26.1683 79.6489 24.3477 81.9617 24.3477C84.2745 24.3477 86.2227 26.1683 86.2227 28.3372C86.2227 30.5062 84.2745 32.3381 81.9617 32.3381C79.6489 32.3381 77.7007 30.5062 77.7007 28.3372ZM83.9441 28.3372C83.9441 27.2471 83.0326 26.3256 81.9617 26.3256C80.8907 26.3256 79.9793 27.2471 79.9793 28.3372C79.9793 29.4274 80.8907 30.3601 81.9617 30.3601C83.0326 30.3601 83.9441 29.4386 83.9441 28.3372Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M27.3604 8.20039C25.8774 8.20039 24.4096 8.47573 23.0387 9.01891C21.6696 9.56022 20.424 10.3544 19.3758 11.3565L18.9884 11.7273L18.9011 11.201C18.4435 8.46262 16.9795 5.96959 14.773 4.16772C12.5646 2.36584 9.75626 1.375 6.85293 1.375H0V6.21496C0 9.30549 1.28362 12.2724 3.56983 14.462C5.85793 16.6516 8.96254 17.8822 12.2001 17.8822H16.0509V29.4127C14.8641 29.9671 14.0419 31.1583 14.0419 32.5388C14.0419 34.4512 15.6142 36.0021 17.5529 36.0021C19.4916 36.0021 21.0639 34.4512 21.0639 32.5388C21.0639 31.1565 20.2417 29.9671 19.053 29.4127V23.0012H23.7944C26.7965 23.0012 29.6732 21.8605 31.7942 19.832C33.9133 17.8035 35.1039 15.0539 35.1039 12.19V8.20226H27.3623L27.3604 8.20039ZM15.768 15.0258H12.202C9.76385 15.0258 7.42448 14.0986 5.70033 12.4485C3.97428 10.7964 3.00207 8.5544 3.00207 6.21496V4.22953H6.85293C9.29104 4.22953 11.6304 5.15669 13.3565 6.80684C15.0825 8.45887 16.0547 10.7009 16.0547 13.0403V15.0258H15.7718H15.768ZM32.1018 11.334V12.1881C32.1018 14.3009 31.2246 16.3275 29.6656 17.8185C28.1067 19.3094 25.9952 20.1467 23.7944 20.1467H19.053V19.0135C19.053 16.9007 19.9303 14.8741 21.4892 13.3831C23.0482 11.8922 25.1597 11.0549 27.3604 11.0549H32.1018V11.334Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M16.1137 2.56608C16.2143 2.64849 16.3074 2.73465 16.4061 2.81894C16.784 2.78897 17.1657 2.77024 17.553 2.77024C21.0982 2.77024 24.349 4.03642 26.8668 6.13236C27.0263 6.12674 27.1859 6.12112 27.3473 6.12112H30.8126C27.6435 2.38065 22.8793 0 17.5511 0C15.9599 0 14.4218 0.217274 12.9597 0.612487C14.0876 1.12383 15.151 1.77752 16.1137 2.5642V2.56608Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M33.2602 21.3209C32.4323 22.1132 31.5132 22.7875 30.5296 23.3381C28.9536 26.483 26.2364 28.976 22.9153 30.289C23.2134 30.9802 23.3786 31.7406 23.3786 32.5386C23.3786 32.7259 23.3691 32.9113 23.3501 33.093C29.1796 31.0439 33.5659 25.9922 34.5951 19.8262C34.1925 20.3544 33.7463 20.8563 33.2602 21.3209Z"
                  fill="#B1B1B1"
                />
                <path
                  d="M3.08573 17.039C3.08573 16.9622 3.08953 16.8873 3.09143 16.8105C2.75154 16.5389 2.42114 16.2542 2.10403 15.9508C1.52299 15.3945 0.998904 14.7895 0.52989 14.1489C0.366589 15.0892 0.277344 16.0538 0.277344 17.039C0.277344 24.4432 5.06623 30.7404 11.7521 33.0911C11.735 32.9075 11.7236 32.724 11.7236 32.5366C11.7236 31.7387 11.8888 30.9783 12.1869 30.2871C6.85874 28.1799 3.08383 23.0384 3.08383 17.039H3.08573Z"
                  fill="#B1B1B1"
                />
              </g>
              <defs>
                <clipPath id="clip0_4003_459">
                  <rect width="88" height="36" fill="white" />
                </clipPath>
              </defs>
            </svg>
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
  padding: 5em 2em 0 2em;
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
