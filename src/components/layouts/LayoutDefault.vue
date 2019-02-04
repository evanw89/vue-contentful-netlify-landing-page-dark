<template>
  <div class="LayoutDefault">
    <div class="d-flex align-items-center p-3 mb-3 mb-md-5">
      <span class="mr-auto">Irrelevant</span>
      <nav class="ml-auto">
        <router-link
          class="p-2 text-white"
          to="/"
        >
          Home
        </router-link> |
        <router-link
          class="p-2 text-white"
          to="/about"
        >
          About
        </router-link>
      </nav>
    </div>
    <main class="LayoutDefault__main mx-auto">
      <slot/>
    </main>
    <footer class="px-5">
      <div class="py-3">
        &copy; Irrelevant
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: `LayoutDefault`,
};
</script>

<style lang="scss">
.LayoutDefault {
  background-color: #222;
  color: #FFF;
}
footer div {
  border-top: 1px solid #aaa;
}

</style>
