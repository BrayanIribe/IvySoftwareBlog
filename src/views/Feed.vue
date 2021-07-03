<template>
  <div>
    <div v-if="false">
      <blog-header v-if="!section" class="markddown-body mb-5"></blog-header>
      <blog-header-section
        v-if="section"
        class="markddown-body mb-5"
      ></blog-header-section>
    </div>

    <div class="d-flex mb-5 align-items-center">
      <div class="mr-3">
        <img
          src="/logo.png"
          style="width: 6rem"
          class="rounded-circle shadow-sm"
        />
      </div>
      <div>
        <h2>Bienvenido</h2>
        <p>
          En este blog podras encontrar interesantes entradas de nuestros
          productos y pasatiempos.
        </p>
      </div>
    </div>

    <p v-if="section" class="text-center display-4 text-capitalize my-5">
      {{ section }}
    </p>

    <div
      class="text-right mb-5 bg-white p-3 border shadow-sm rounded"
      v-for="entry in displayPosts"
      :key="entry.id"
    >
      <router-link
        tag="h3"
        class="text-left m-0 p-0 link text-primary"
        :to="{ path: `${entry.section}/${entry.id}` }"
        >{{ entry.title }}</router-link
      >

      <p class="text-muted m-0 p-0">{{ entry.date }}</p>
      <router-link
        v-if="!section"
        tag="h6"
        class="m-0 p-0 link"
        :to="{ path: `${entry.section}` }"
        >#{{ entry.section }}</router-link
      >

      <p class="font-weight-light text-left text-justify mt-1">
        {{ entry.description }}
      </p>
    </div>

    <div class="bg-white rounded border shadow-sm p-3" v-if="totalPages > 1">
      <b-pagination
        class="pagination m-0 p-0"
        align="center"
        v-model="currentPage"
        :total-rows="rows"
        :per-page="perPage"
      ></b-pagination>
    </div>
  </div>
</template>

<script>
import blogHeader from "@/components/blogHeader.md";
import blogHeaderSection from "@/components/blogHeaderSection.md";

export default {
  name: "home",
  props: ["section"],
  metaInfo({ section }) {
    return {
      title: section || "Inicio",
    };
  },
  components: {
    blogHeader,
    blogHeaderSection,
  },
  data() {
    return {
      perPage: parseInt(this.$store.state.VUE_APP_POSTS_PER_PAGE, 10),
      currentPage: 1,
    };
  },
  computed: {
    allPosts() {
      return this.section
        ? this.$store.state.postsIndex.filter(
            (post) => post.section === this.section
          )
        : this.$store.state.postsIndex;
    },
    totalPages() {
      const { rows, perPage } = this;
      return Math.round(rows / perPage) + 1;
    },
    rows() {
      return this.allPosts.length;
    },
    displayPosts() {
      const skip =
        this.currentPage > 1 ? (this.currentPage - 1) * this.perPage : 0;
      const limit = skip + this.perPage;
      return this.section
        ? this.allPosts
            .filter((post) => post.section === this.section)
            .slice(skip, limit)
        : this.allPosts.slice(skip, limit);
    },
  },
};
</script>
