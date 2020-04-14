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

      <div class="row recent-posts" v-if="page.posts">
        <div class="col-sm-4" v-for="post in page.posts" :key="post.permalink">
          <div class="mt-0">
            <saber-link
              :to="post.attributes.permalink"
              :title="`Read ${post.attributes.title}`"
              class="text-black font-extrabold"
            >
              <img
                class="mb-2"
                :src="post.assets.thumbnail"
                :alt="`Afbeelding van ${post.attributes.title}`">
              <br/>
              {{ post.attributes.title }}
            </saber-link>
            <br />
            <small class="my-2">
              {{ formatDate(post.attributes.createdAt) }}
            </small>
            <br />
            <p class="category">{{ post.attributes.categories[0].split('-')[0] }}</p>
          </div>
          <!-- <p class="excerpt" v-html="post.attributes.excerpt"></p> -->
        </div>
      </div>

      <div class="row">
        <div class="col">
          <ul>
            <li v-if="page.prevPost">
              <router-link :to="page.prevPost.permalink">
                Previous: {{ page.prevPost.title }}
              </router-link>
            </li>
            <li v-if="page.nextPost">
              <router-link :to="page.nextPost.permalink">
                Next: {{ page.nextPost.title }}
              </router-link>
            </li>
          </ul>
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
    Footer,
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

.category {
  font-size: 12px;
  color: grey;
  text-transform: capitalize;
}

// .excerpt {
//   font-size: 14px;
//   line-height: 24px;
// }

.recent-posts {
  ul {
    margin: 0;
    padding-left: 0;
    list-style: none;
  }
  a {
    color: #88c441;
  }
}
</style>
