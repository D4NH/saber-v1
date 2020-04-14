<template>
  <div>
    <Navbar />
    <div class="container">
      <div class="row">
        <div class="col">
          <img class="img-fluid mb-3" :src="page.assets.cover" alt="cover" />
          <slot name="default" />
        </div>
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
import Navbar from "../components/Navbar.vue";
import Footer from "../components/Footer.vue";

export default {
  components: {
    Navbar,
    Footer
  },
  head() {
    const pageTitle = this.page.title;
    return {
      title: pageTitle
        ? `${pageTitle} - ${this.$siteConfig.title}`
        : this.$siteConfig.title,
    };
  },
  props: ["page"],
  methods: {
    formatDate(v) {
      const date = new Date(v);
      return `${date.getFullYear()}-${date.getMonth() + 1}-${date.getDate()}`;
    },
  },
};
</script>

<style lang="scss" scoped>
img[src*="#fluid"] {
  max-width: 100%;
  height: auto;
}

a {
  color: #88c441;
}
</style>
