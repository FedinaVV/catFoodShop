<template>
  <div class="catalog-food">
    <div class="container">
      <h1 class="catalog-food__title">Ты сегодня покормил кота?</h1>
      <div class="catalog-food__wrapper">
        <div v-for="item in infoCatalog" :key="item.id">
          <div v-if="item.quantity !== 0" v-bind:class="{ active: item.isChecked }" class="catalog-food__item">
            <div v-bind:class="{ active: item.isChecked }" @click="item.isChecked = !item.isChecked"
                 class="catalog-food__wrapper-item">
              <p class="catalog-food__desc">Сказочное заморское яство</p>
              <p v-if="item.isChecked" class="catalog-food__desc-hover">Котэ не одобряет?</p>
              <h2 class="catalog-food__heading">Нямушка</h2>
              <p class="catalog-food__flavor">{{ item.flavor }}</p>
              <p class="catalog-food__servings">{{ item.servings }}</p>
              <p class="catalog-food__present">{{ item.present }}</p>
              <p class="catalog-food__feedback">{{ item.feedback }}</p>
              <div class="catalog-food__wrapper-img">
                <img src="@/assets/images/cat.png" alt="Cat">
              </div>
              <div v-bind:class="{ active: item.isChecked }" class="catalog-food__weight">{{ item.weight }}</div>
            </div>
            <div v-if="item.isChecked" class="catalog-food__characteristic">{{ item.characteristic }}</div>
            <div v-if="!item.isChecked" class="catalog-food__buy">Чего сидишь? Порадуй котэ,
              <a href="#!" class="catalog-food__buy-link" @click="item.isChecked = !item.isChecked">купи.</a>
            </div>
          </div>
          <div v-if="item.quantity === 0" class="catalog-food__item catalog-food__item-soldOut">
            <div class="catalog-food__wrapper-item catalog-food__wrapper-item-soldOut">
              <p class="catalog-food__desc catalog-food__desc-soldOut">Сказочное заморское яство</p>
              <h2 class="catalog-food__heading catalog-food__heading-soldOut">Нямушка</h2>
              <p class="catalog-food__flavor">{{ item.flavor }}</p>
              <p class="catalog-food__servings catalog-food__servings-soldOut">{{ item.servings }}</p>
              <p class="catalog-food__present catalog-food__present-soldOut">{{ item.present }}</p>
              <p class="catalog-food__feedback catalog-food__feedback-soldOut">{{ item.feedback }}</p>
              <div class="catalog-food__wrapper-img">
                <img src="@/assets/images/cat.png" alt="Cat">
              </div>
              <div class="catalog-food__weight catalog-food__weight-soldOut">{{ item.weight }}</div>
            </div>
            <div class="catalog-food__soldOut">Печалька, {{ item.flavor }} закончился.</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      infoCatalog: [
        {
          id: 1,
          flavor: 'с фуа-гра',
          servings: '10 порций',
          present: 'мышь в подарок',
          feedback: "\u00A0",
          weight: '0,5',
          quantity: 1,
          isChecked: false,
          characteristic: 'Печень утки разварная с артишоками.'
        },
        {
          id: 2,
          flavor: 'с рыбой',
          servings: '40 порций',
          present: '2 мыши в подарок',
          feedback: "\u00A0",
          weight: '2',
          quantity: 2,
          isChecked: false,
          characteristic: 'Головы щучьи с чесноком да свежайшая сёмгушка.'
        },
        {
          id: 3,
          flavor: 'с курой',
          servings: '100 порций',
          present: '5 мышей в подарок',
          feedback: 'заказчик доволен',
          weight: '5',
          quantity: 0,
          isChecked: false,
          characteristic: 'Филе из цыплят с трюфелями в бульоне.'
        }
      ]
    }
  }
}
</script>

<style lang="scss">
@import "assets/styles/styles.scss";
</style>
