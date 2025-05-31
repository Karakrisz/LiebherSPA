<script setup>
// Egy példatömb a szolgáltatásokról. A valós projektben ez lehet adatbázisból,
// CMS-ből vagy API-ból jön, de most bemutatásképpen itt van „hardcode”-olva.
const services = [
  {
    id: 1,
    title: 'Épületbontás',
    description:
      'Kézi és gépi bontási munkák, beleértve a pulverizátorral való bontást és törőfejezést.',
    image: '/img/test.jpg',
    // link: '/szolgaltatasok/epuletbontas',
  },
  {
    id: 2,
    title: 'Földmunka',
    description: 'Teljes körű földmunkák, lyukfúrás, tuskózás és ágrarás.',
    image: '/img/test.jpg',
    // link: '/szolgaltatasok/foldmunka',
  },
  {
    id: 3,
    title: 'Közműfektetés',
    description:
      'Szakértői csapatunkkal vállaljuk közművek fektetését és kapcsolódó munkálatokat.',
    image: '/img/test.jpg',
    // link: '/szolgaltatasok/kozmufektetes',
  },
  {
    id: 4,
    title: 'Térkövezés és kőműves munkák',
    description:
      'Minőségi térkövezés, játszóterek és kültéri fitnessparkok kivitelezése.',
    image: '/img/test.jpg',
    // link: '/szolgaltatasok/terkozes-komuves',
  },
  {
    id: 5,
    title: 'Kertépítés',
    description:
      'Komplett kertépítési szolgáltatások, beleértve az esővíztartályok telepítését.',
    image: '/img/test.jpg',
    // link: '/szolgaltatasok/kertepites',
  },
  {
    id: 6,
    title: 'Szállítás',
    description:
      'Sitt, zöldhulladék és szemét szállítása megbízhatóan és gyorsan.',
    image: '/img/test.jpg',
    // link: '/szolgaltatasok/szallitas',
  },
]
</script>

<template>
  <section class="services" aria-labelledby="services-heading">
    <div class="container">
      <!-- Szolgáltatások címe -->
      <h2 id="services-heading" class="services__heading">Szolgáltatásaink</h2>

      <!-- Szolgáltatások listája -->
      <ul class="services__list">
        <li
          v-for="service in services"
          :key="service.id"
          class="services__list-item"
        >
          <!-- Minden szolgáltatás egy link, ami a részletes oldalra mutat -->
          <NuxtLink
            :to="service.link"
            class="services__item"
            :aria-label="service.title"
          >
            <!-- Háttérkép div, CSS-ben állítjuk be a BG-image-et -->
            <div
              class="services__item-background"
              :style="{ backgroundImage: `url(${service.image})` }"
            ></div>
            <!-- Szöveges tartalom -->
            <div class="services__item-content">
              <h3 class="services__item-title">{{ service.title }}</h3>
              <p class="services__item-description">
                {{ service.description }}
              </p>
            </div>
          </NuxtLink>
        </li>
      </ul>

      <!-- „Összes szolgáltatás” gomb -->
      <div class="services__actions">
        <NuxtLink to="/szolgaltatasok" class="services__button">
          Összes szolgáltatás
        </NuxtLink>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.services {
  padding: 5.3em 0 5em 0;
  text-align: center;
  /* ---- CÍM ---- */
  &__heading {
    text-align: center;
    font-size: 2rem;
    font-weight: 700;
    position: relative;
    display: inline-block;
    margin: 0 auto 2.5em;

    /* Sárga aláhúzás a cím alatt */
    &::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: -0.6em;
      width: 9.7em;
      height: 0.5em;
      background-color: #ffd51e; /* Liebher sárga */
      z-index: -1;
    }
  }

  /* ---- LISTA ---- */
  &__list {
    display: grid;
    grid-template-columns: 1fr; /* alapból 1 oszlop (mobil) */
    gap: 2rem;
    list-style: none;
    padding: 0;
    margin: 0;

    /* Ha a képernyő legalább 768px széles, legyen 2 oszlop */
    @media (min-width: 768px) {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  &__list-item {
    /* nincs külön speciális stílus, a belső .services__item kezeli a kártya kinézetét */
  }

  /* ---- SZOLGÁLTATÁS KÁRDSÉT ---- */
  &__item {
    position: relative;
    display: block;
    height: 200px;
    color: #ffffff;
    text-decoration: none;
    border-radius: 0.5rem;
    overflow: hidden;
    transition: transform 0.3s ease;

    &:hover {
      transform: translateY(-4px);
    }

    /* Háttérkép DIV (CSS-ben állítjuk be a background-image-et) */
    &-background {
      position: absolute;
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;
      background-size: cover;
      background-position: center;
      filter: brightness(0.25); /* sötétebb overlay érzés */
      transition: filter 0.3s ease;
    }

    /* Szöveges konténer a kártya tetején */
    &-content {
      position: relative;
      z-index: 1;
      padding: 1.5rem;
      display: flex;
      flex-direction: column;
      justify-content: center;
      height: 100%;
      text-align: left;
    }

    &-title {
      font-size: 1.25rem;
      font-weight: 700;
      margin: 0 0 0.5rem;
    }

    &-description {
      font-size: 0.9rem;
      margin: 0;
      line-height: 1.4;
      width: 60%;
    }
  }

  /* ---- AKCIÓ GOMBOK ---- */
  &__actions {
    margin-top: 3rem;
    text-align: center;
  }

  &__button {
    display: inline-block;
    padding: 0.75rem 1.5rem;
    background-color: #000000;
    color: #ffffff;
    border-radius: 0.375rem;
    text-decoration: none;
    font-size: 1rem;
    font-weight: 500;
    transition: background-color 0.2s ease;

    &:hover {
      background-color: #333333;
    }
  }
}

/* Container segítségével középre igazítjuk a tartalmat nagyobb képernyőn */
.container {
  max-width: 1200px;
  margin: 0 auto;
}
</style>
