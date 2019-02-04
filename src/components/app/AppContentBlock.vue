<template>
  <div class="AppContentBlock">
    <div class="AppContentBlock__body">
      <h2 class="mb-3">{{ title }}</h2>
    </div>
    <div
      v-if="image"
      :class="{ 'AppContentBlock__figure--left': position === `left` }"
      class="AppContentBlock__figure"
    >
      <img
        :src="imageSrc"
        :srcset="imageSrcset"
      >
      <div class="AppContentBlock__text">
        <p class="px-5 pt-5 pb-3">{{ text }}</p>
        <div class="text-center bg-white pb-5">
          <button class="btn btn-lg btn-outline-info">Learn More</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { TimelineMax } from 'gsap';
export default {
  name: `AppContentBlock`,
  props: {
    image: {
      type: Object,
      default: null,
    },
    position: {
      type: String,
      default: `right`,
    },
    text: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
  },
  computed: {
    imageSrc() {
      if (!this.image) return null;
      return `${this.image.url}?w=360&h=250&fit=thumb&fm=jpg&fl=progressive&q=70`;
    },
    imageSrcset() {
      if (!this.image) return null;
      return `${this.image.url}?w=720&h=500&fit=thumb&fm=jpg&fl=progressive&q=40 2x`;
    },
  },
  mounted() {
    const tl = new TimelineMax()
    .staggerFromTo(".AppContentBlock > div", 0.4, {
          opacity: 0
        }, {
          opacity: 1
        },
    0.07, 0.4)
  }
};
</script>

<style lang="scss">
.AppContentBlock {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  text-align: center;
  align-content: flex-start;
  background-color: #FFF;
  flex: 1;
  transform: translateY(-8rem);
  padding: 3rem 0;

  &__body,
  &__figure {
    border-left: 3px solid #f1f1f1;
    order: -1;
    padding: 0 2rem;
  }

  &__body {
    flex-grow: 9999;
    flex-basis: 24em;
  }

  &__figure {
    flex-grow: 1;
    flex-basis: 18em;
    text-align: center;

    img {
      max-width: 90%;
    }
  }

  &__figure:hover &__text {
      opacity: 1;
  }

  &:first-child &__body,
  &:first-child &__figure {
    border: none
  }

  &__text {
    position: absolute;
    left: 0;
    width: 100%;
    background-color: #FFF;
    transform-origin: top center;
    transition: opacity 0.3s ease;
    opacity: 0;
  }
}
.About__content-blocks .AppContentBlock {
  transform: initial;
  background: none;
  margin-bottom: 0!important;
  padding-top: 1.5rem;

  img {
    margin-bottom: 1rem;
  }

  *:not(.btn) {
    border: none;
  }

  &__text {
    position: initial;
    background: none;
    opacity: 1;
    text-align: left;

    * {
      padding: 0!important;
      background: none!important;
    }

    .btn {
      display: none;
    }
  }
}
@media (max-width: 792px) {
  .AppContentBlock__figure--left {
    order: -1;
  }
}
</style>
