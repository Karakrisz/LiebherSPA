<script setup>
// Segédfüggvény: visszaadja, hogy a index páros-e (0‐tól indulunk),
// így a 2., 4. … elemnél true → fordított („reverse”) elrendezés az asztalin.
const isEven = (idx) => idx % 2 === 1

// Mintaadatok; a valós projektben jöhetnek API-ból, CMS-ből vagy más állományból.
// Az image útvonalai a /public/images/fleet/ mappára mutatnak.
const machines = [
  {
    id: 1,
    title: 'Láncos kotrógépek (3,5–23 tonnáig)',
    available: true,
    // count: 5, // pl. 5 darab elérhető
    image: '/img/test.jpg',
    description:
      'A lánctalpas kotrógépek kiválóan alkalmasak nehéz terepen végzett földmunkákhoz. Lánctalpas kialakításuknak köszönhetően stabilak és jól mozognak egyenetlen, puha talajon is. Ideálisak mély ásásokhoz, bontási munkákhoz és nagy mennyiségű anyag mozgatásához.',
  },
  {
    id: 2,
    title: 'Kombigépek (Kotró‐rakodó)',
    available: true,
    // count: 3,
    image: '/img/test.jpg',
    description:
      'A kombigépek, más néven kotró‐rakodók, sokoldalú munkagépek, amelyek egyesítik a kotrógép és a rakodógép funkcióit. Elöl homlokrakodó kanállal, hátul pedig kotrókarral rendelkeznek, így alkalmasak ásásra, rakodásra és anyagmozgatásra egyaránt.',
  },
  {
    id: 3,
    title: 'Dömperek',
    available: false,
    // count: 0,
    image: '/img/test.jpg',
    description:
      'A dömperek billenőplatós tehergépkocsik, amelyek elsősorban anyagszállításra szolgálnak. Képesek nagy mennyiségű föld, törmelék vagy egyéb anyag gyors és hatékony szállítására és lerakására.',
  },
  {
    id: 4,
    title: 'Úthengerek',
    available: false,
    // count: 0,
    image: '/img/test.jpg',
    description:
      'Az úthenger talajtömörítő gép, amelyet az építőiparban utak és alapozások építésére használnak. A hengerek súlyuk és esetleges vibrációs funkciójuk révén tömörítik a talajt vagy az aszfaltot, biztosítva az alapok stabilitását.',
  },
  {
    id: 5,
    title: 'Billencs teherautó',
    available: false,
    // count: 0,
    image: '/img/test.jpg',
    description:
      'A billencs teherautók olyan járművek, amelyek platója hidraulikusan billenthető, így lehetővé teszik az anyag gyors lerakását. Különösen hasznosak építkezéseken és tereprendezési munkáknál.​',
  },
]
</script>

<template>
  <section class="fleet" aria-labelledby="fleet-heading">
    <div class="container">
      <!-- 1. Szekció címe -->
      <h2 id="fleet-heading" class="fleet__heading">Gépparkunk</h2>

      <!-- 2. Gép lista -->
      <ul class="fleet__list">
        <li
          v-for="(machine, index) in machines"
          :key="machine.id"
          :class="[
            'fleet__list-item',
            { 'fleet__list-item--reverse': isEven(index) },
          ]"
        >
          <!-- Kép -->
          <div class="fleet__image">
            <img
              :src="machine.image"
              :alt="machine.title"
              width="560"
              height="350"
            />
          </div>

          <!-- Leírás -->
          <div class="fleet__content fleet__content--right">
            <h3 class="fleet__item-title">
              {{ machine.title }}
            </h3>

            <!-- Elérhetőség jelző -->
            <div
              class="fleet__availability"
              :class="{
                'fleet__availability--available': machine.available,
                'fleet__availability--unavailable': !machine.available,
              }"
            >
              <span class="fleet__dot"></span>
              <!-- <span class="fleet__status-text">
                {{
                  machine.available
                    ? `${machine.count} db elérhető`
                    : 'Jelenleg nem elérhető'
                }}
              </span> -->
            </div>

            <!-- Részletes leírás -->
            <p class="fleet__description">
              {{ machine.description }}
            </p>

            <!-- Kibérlem gomb -->
            <NuxtLink
              to="/#kapcsolat"
              class="fleet__button"
              aria-label="Kibérem {{ machine.title }}"
            >
              Kibérlem
            </NuxtLink>
          </div>
        </li>
      </ul>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.fleet {
  padding: 5em 0 5em 0;
  text-align: center;
  background-color: #f6f6f6;

  /* ---- 1. Szekció címe ---- */
  &__heading {
    text-align: center;
    font-size: 2rem;
    font-weight: 700;
    display: inline-block;
    position: relative;
    margin: 0 auto 2.5em;
    z-index: 1;

    &::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: -0.6em;
      width: 7.7em;
      height: 0.5em;
      background-color: #ffd51e; /* Liebher sárga */
      z-index: -1;
    }
  }

  /* ---- 2. Lista (ul/li) ---- */
  &__list {
    list-style: none;
    padding: 0;
    margin: 0;

    display: flex;
    flex-direction: column;
    gap: 3rem;

    > *:nth-child(1) {
      text-align: left;
    }

    > *:nth-child(2) {
      text-align: end;
    }

    > *:nth-child(3) {
      text-align: left;
    }

    > *:nth-child(4) {
      text-align: end;
    }

    > *:nth-child(5) {
      text-align: left;
    }
  }

  /* ---- 3. Egy-egy gép (li) ---- */
  &__list-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1.5rem;

    /* Asztali nézetben kétoszlopos, alternáló elrendezés */
    @media (min-width: 768px) {
      flex-direction: row;
      align-items: center;
      gap: 2rem;

      /* Ha --reverse, akkor a kép és szöveg megfordul */
      &.fleet__list-item--reverse {
        flex-direction: row-reverse;
      }
    }

    /* A blokk körül határoló vonal (opcionális) */
    & + & {
      border-top: 1px solid #dcdcdc;
      padding-top: 3rem;
    }
  }

  /* ---- 4. Kép konténer ---- */
  &__image {
    flex: 1 1 50%;
    width: 100%;
    max-width: 560px;
    border-radius: 0.5rem;
    overflow: hidden;

    img {
      display: block;
      width: 100%;
      height: auto;
      object-fit: cover;
      border-radius: 0.5rem;
    }
  }

  /* ---- 5. Szöveges tartalom ---- */
  &__content {
    flex: 1 1 50%;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    gap: 1rem;
  }

  &__item-title {
    font-size: 1.5rem;
    font-weight: 700;
    margin: 0;
  }

  /* ---- 6. Elérhetőség jelző ---- */
  &__availability {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    font-size: 0.9rem;
    font-weight: 500;

    &-available .fleet__dot {
      background-color: #28a745; /* zöld */
    }
    &-unavailable .fleet__dot {
      background-color: #dc3545; /* piros */
    }

    .fleet__dot {
      display: inline-block;
      width: 0.75rem;
      height: 0.75rem;
      border-radius: 50%;
    }

    .fleet__status-text {
      color: #333333;
    }
  }

  /* ---- 7. Leírás ---- */
  &__description {
    font-size: 1rem;
    line-height: 1.5;
    color: #555555;
    margin: 0;
  }

  /* ---- 8. „Kibérlem” gomb ---- */
  &__button {
    display: inline-block;
    margin-top: 1rem;
    padding: 0.75rem 1.5rem;
    background-color: #ff6d00; /* narancs */
    color: #ffffff;
    border-radius: 0.375rem;
    text-decoration: none;
    font-size: 1rem;
    font-weight: 500;
    text-align: center;
    transition: background-color 0.2s ease;
    width: max-content;

    &:hover {
      background-color: #e65c00;
    }
  }
}

/* Container csak arra szolgál, hogy középre igazítsa a szakasz tartalmát nagyobb képernyőn */
.container {
  max-width: 1200px;
  margin: 0 auto;
}
</style>
