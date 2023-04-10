<script>
import SpacePageVue from './views/SpacePage.vue'

export default {
  name: 'App',
  components: {
    SpacePageVue
  }
}
</script>

<template>
  <div class="app-container">
    <header class="app-container__header">
      <h1>Natural History Museum</h1>
      <nav class="app-container__header__menu">
        <div>Home</div>
        <div>Dinosaurs</div>
        <div>Space</div>
        <div>Oceans</div>
        <div>Wildlife</div>
      </nav>
    </header>
    <div class="app-container__component">
      <SpacePageVue />
    </div>
  </div>
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Marcellus&family=Orbitron:wght@400;500;600;800&family=Roboto:wght@300;400;500&display=swap');

$primary-color: #323233;
$secondary-color: #3ddab8;

.app-container {
  display: flex;
  flex-direction: column;
  font-family: 'Roboto', sans-serif;
  overflow-x: hidden;

  &__header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px;
    background-color: $primary-color;
    color: #fff;

    h1 {
      font-family: 'Marcellus';
      font-weight: 600;
      font-size: 24px;
      margin: 0;
    }

    &__menu {
      display: flex;
      gap: 20px;
      font-size: 1rem;

      div {
        cursor: pointer;
        transition: color 0.3s ease-in-out;

        &:hover {
          color: $secondary-color;
        }
      }
    }
  }

  &__component {
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #eee;
    min-height: 100vh;
    max-width: 100vw;
  }

  @media screen and (max-width: 767px) {
    &__header {
      flex-direction: column;

      h1 {
        margin-bottom: 10px;
      }

      &__menu {
        margin-top: 10px;
      }
    }
  }

  @media screen and (max-width: 480px) {
    &__header {
      h1 {
        font-size: 1.4rem;
      }

      &__menu {
        font-size: 0.8rem;

        div {
          padding: 5px;
        }
      }
    }
  }
}
</style>
