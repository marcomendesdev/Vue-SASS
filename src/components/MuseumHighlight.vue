<template>
  <div class="museum-highlight">
    <h1 class="museum-highlight__title">Space</h1>
    <div class="museum-highlight__component">
      <div
        :class="{
          'museum-highlight__highlights': highlight.description,
          'museum-highlight__highlights--info': highlight.info
        }"
        v-for="highlight in museumHighlights"
        :key="highlight.name"
      >
        <div class="museum-highlight__highlights__badge" v-for="badge in badgeImage" :key="badge">
          <img :src="badge" alt="New" />
        </div>
        <img :src="highlight.image" alt="image" />
        <div class="museum-highlight__highlights__body">
          <div class="museum-highlight__highlights__body__header">
            <h3 v-if="highlight.name">{{ highlight.name }}</h3>
            <p v-if="highlight.date">{{ highlight.date }}</p>
            <p v-if="highlight.createdAt">{{ highlight.createdAt }}</p>
          </div>
          <p v-if="highlight.description">{{ highlight.description }}</p>

          <p v-if="highlight.info">{{ highlight.info }}</p>
          <div
            class="museum-highlight__highlights__body__extra"
            v-for="news in highlight"
            :key="news.title"
          >
            <p v-if="news.title">{{ news.title }}</p>
            <p v-if="news.date">{{ news.date }}</p>
          </div>
          <a v-if="highlight.quiz" :href="highlight.quiz">Quiz</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MuseumHighlight',
  props: {
    museumHighlights: {
      type: Array,
      required: true
    },
    badgeImage: {
      type: Array,
      required: true
    }
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Marcellus&family=Orbitron:wght@400;500;600;800&family=Roboto:wght@300;400;500&display=swap');

.museum-highlight {
  width: 100%;
  &__title {
    color: #2c3791;
    font-size: 34px;
    padding: 50px;
    font-family: 'Orbitron', sans-serif;
    font-weight: 800;
  }
  &__component {
    padding: 20px;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    grid-gap: 20px;
  }

  &__highlights {
    position: relative;
    background-color: #fff;
    max-height: 300px;

    min-width: 300px;
    padding: 0px;
    margin: 10px;
    border-radius: 5px;
    box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.2);
    font: 300 0.9rem/1 'Roboto', sans-serif;
    color: #2c3791;

    &__badge {
      position: absolute;
      top: -12px;
      right: -10px;
      width: 30px;
      height: 30px;
      display: flex;
      justify-content: center;
      align-items: center;

      img {
        width: 30px !important;
        height: 30px !important;
      }
    }

    &__body {
      padding: 10px;
      h3 {
        font-size: 1rem;
        font-weight: 500;
        margin: 0px;
      }
      p {
        margin: 0 0 10px;
        font-weight: 400;
      }
      a {
        display: inline-block;
        text-align: center;
        width: 100%;
        color: #fff;
        font-weight: 500;
        text-decoration: none;
        background-color: #037beb;
        margin-top: 0px;
        padding: 5px 0px;
        border-radius: 5px;
        box-shadow: 0px 0px 5px 0px rgba(0, 0, 0, 0.4);
      }

      &__header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 10px;

        p {
          font-size: 0.8rem;
          font-weight: 300;
        }
      }

      &__extra {
        color: rgb(134, 3, 20);
        display: flex;
        p {
          font-size: 0.8rem;
          font-weight: 500;
        }
      }
    }

    img {
      width: 100%;
      height: 140px;
      object-fit: cover;
      border-radius: 5px 5px 0px 0px;
    }
  }

  &__highlights--info {
    @extend .museum-highlight__highlights;
    background-color: #440b74;
    color: #fff;

    &__badge {
      @extend .museum-highlight__highlights__badge;
    }
  }
}
</style>
