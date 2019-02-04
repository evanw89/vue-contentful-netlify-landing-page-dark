<template>
  <div class="AppTeaser">
    <div class="card-body px-3">
      <h5 class="card-title text-center">{{ title }}</h5>
      <img
        class="card-img-top my-3"
        :src="imageSrc"
        :srcset="imageSrcset"
        >
      <p class="card-text">{{ text }}</p>
      
      <a
        :href="link"
        class="btn btn-outline-info py-3 w-100"
      >
        Read more
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: `AppTeaser`,
  props: {
    image: {
      type: Object,
      default: null,
    },
    link: {
      type: String,
      default: '',
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
      return `${this.image.url}?w=256&h=160&fit=thumb&fm=jpg&fl=progressive&q=70`;
    },
    imageSrcset() {
      if (!this.image) return null;
      return `${this.image.url}?w=512&h=320&fit=thumb&fm=jpg&fl=progressive&q=40 2x`;
    },
  },
};
</script>

<style scoped lang="scss">
  .AppTeaser {
    transition: 0.3s ease;
    
    &:hover {
      transform: translateY(-5px);
      background-color: #393939;
    }
  }
</style>