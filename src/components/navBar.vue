  <template>
  <div>
    <b-navbar type="dark" toggleable="sm" variant="primary" fixed="top">
      <b-navbar-brand href="#" @click="$router.push({name: 'home'})">IvySoftware</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav class="ml-auto mr-sm-5">
          <b-nav-item v-for="(section, index) in sections" :key="index" href="#" @click="$router.push({path: `/${section}`})" class="text-capitalize">{{ section }}</b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script language="ts">
export default {
  name: "nav-bar",
  data() {
    return {
      sections: Array.from(new Set(this.$store.state.postsIndex
        .map(post => post.section)))
    };
  }
};
</script>

<style>
/* Custom SCSS here */

.github-ribbon a {
  background-color: #404d61 !important;
}
</style>