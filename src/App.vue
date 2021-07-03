<template>
  <div id="app">
    <nav-bar></nav-bar>
    <div class="container pt-5">
      <router-view :key="$route.path"></router-view>
    </div>
    <TopButton />
    <Footer v-if="false"></Footer>
  </div>
</template>

<script language="ts">
import navBar from "@/components/navBar.vue";
import Footer from "@/components/Footer.vue";
import TopButton from "@/components/TopButton.vue";

export default {
  metaInfo: {
    title: "Loading...",
    titleTemplate: "%s | TecPyme Blog",
    meta: [
      { name: "description", content: "TecPyme Blog" },
      { name: "og:title", content: "TecPyme Blog" },
      {
        name: "keywords",
        content: "VueJS, blog-engine, markdown-article, github-pages, tecpyme",
      },
    ],
  },
  components: {
    navBar,
    Footer,
    TopButton,
  },
  created() {},
};
</script>

<style lang="scss">
/* Custom SCSS here */

html {
  scroll-padding-top: 80px; /* height of sticky header */
}

html,
body,
#app {
  background-color: #ececec;
  padding-top: 1rem;
}
.nav-bar {
  background-color: #007bff;
}

h1,
h3 {
  color: #007bff;
  font-weight: normal;
}

.link {
  cursor: pointer;
  &:hover {
    text-decoration: underline;
  }
}

.page-link {
  color: #007bff;
}

.page-item.active .page-link {
  border-color: #007bff;
  background-color: #007bff;
}

.post img {
  max-width: 95%;
  vertical-align: middle;
  border: 0;
}

@media only screen and (max-width: 576px) {
  .post img {
    max-width: 95%;
    vertical-align: middle;
    border: 0;
  }
}

.post iframe {
  max-width: 95%;
  vertical-align: middle;
  border: 0;
}

.post p {
  margin: 1.2rem 0;
  text-align: justify;
}
.post h4 {
  margin-bottom: 3rem;
  color: #404d61;
}

.fade-enter-active,
.fade-leave-active {
  transition-duration: 0.3s;
  transition-property: opacity;
  transition-timing-function: ease;
}

.fade-enter,
.fade-leave-active {
  opacity: 0;
}

.fl-container {
  width: 100%;
  height: 72vh;
  display: flex;
  align-items: center;
}
</style>
