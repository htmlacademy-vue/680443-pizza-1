<template>
  <section>
    <header class="header">
      <div class="header__logo">
        <a href="#" class="logo">
          <img src="~@/assets/img/logo.svg" alt="V!U!E! Pizza logo" width="90" height="40">
        </a>
      </div>
      <div class="header__cart">
        <a href="#">0 ₽</a>
      </div>
      <div class="header__user">
        <a href="#" class="header__login"><span>Войти</span></a>
      </div>
    </header>
    <main class="content">
      <form action="#" method="post">

        <div class="content__wrapper">
          <h1 class="title title--big">Конструктор пиццы</h1>

          <div class="content__dough">

            <div class="sheet">
              <h2 class="title title--small sheet__title">Выберите тесто</h2>

              <div class="sheet__content dough">
                <label
                  v-for="(item, i) in pizza.dough"
                  :key="item.id"
                  :class="`dough__input dough__input--${PIZZA_SIZES[i+1]}`"
                >
                  <input type="radio" name="dought" :value="item.size" class="visually-hidden" checked>
                  <b>{{ item.name }}</b>
                  <span>{{ item.description }}</span>
                </label>
              </div>

            </div>

          </div>

          <div class="content__diameter">
            <div class="sheet">
              <h2 class="title title--small sheet__title">Выберите размер</h2>

              <div class="sheet__content diameter">
                <label
                  v-for="(size, i) in pizza.sizes"
                  :key="size.id"
                  :class="`diameter__input diameter__input--${PIZZA_DIAMETERS[i+1]}`"
                >
                  <input type="radio" name="diameter" :value="size.diameter" class="visually-hidden">
                  <span>{{ size.name }}</span>
                </label>
              </div>
            </div>
          </div>

          <div class="content__ingredients">
            <div class="sheet">
              <h2 class="title title--small sheet__title">Выберите ингредиенты</h2>

              <div class="sheet__content ingredients">

                <div class="ingredients__sauce">
                  <p>Основной соус:</p>

                  <label
                    v-for="sauce in pizza.sauces"
                    :key="sauce.id"
                    class="radio ingredients__input"
                  >
                    <input type="radio" name="sauce" value="tomato" checked>
                    <span>{{ sauce.name }}</span>
                  </label>
                </div>

                <div class="ingredients__filling">
                  <p>Начинка:</p>

                  <ul class="ingredients__list">
                    <li
                      v-for="(ingredient, i) in pizza.ingredients"
                      :key="ingredient.id"
                      class="ingredients__item"
                    >
                      <span :class="`filling filling--${PIZZA_INGREDIENTS[i+1]}`">{{ ingredient.name }}</span>

                      <div class="counter counter--orange ingredients__counter">
                        <button type="button" class="counter__button counter__button--minus" disabled>
                          <span class="visually-hidden">Меньше</span>
                        </button>
                        <input type="text" name="counter" class="counter__input" value="0">
                        <button type="button" class="counter__button counter__button--plus">
                          <span class="visually-hidden">Больше</span>
                        </button>
                      </div>
                    </li>
                  </ul>

                </div>

              </div>
            </div>
          </div>

          <div class="content__pizza">
            <label class="input">
              <span class="visually-hidden">Название пиццы</span>
              <input type="text" name="pizza_name" placeholder="Введите название пиццы">
            </label>

            <div class="content__constructor">
              <div class="pizza pizza--foundation--big-tomato">
                <div class="pizza__wrapper">
                  <div class="pizza__filling pizza__filling--ananas"></div>
                  <div class="pizza__filling pizza__filling--bacon"></div>
                  <div class="pizza__filling pizza__filling--cheddar"></div>
                </div>
              </div>
            </div>

            <div class="content__result">
              <p>Итого: 0 ₽</p>
              <button type="button" class="button" disabled>Готовьте!</button>
            </div>
          </div>

        </div>

      </form>
    </main>
  </section>
</template>

<script>
import misc from '@/static/misc.json'
import pizza from '@/static/pizza.json'
import user from '@/static/user.json'
import {PIZZA_SIZES, PIZZA_DIAMETERS, PIZZA_INGREDIENTS} from '@/common/constants'

export default {
  name: "Index.vue",
  data () {
    return {
      misc,
      pizza,
      user,
      PIZZA_SIZES,
      PIZZA_DIAMETERS,
      PIZZA_INGREDIENTS
    }
  }
}
</script>

<style scoped>

</style>
