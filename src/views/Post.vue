<script>
import VueWithCompiler from "vue/dist/vue.esm";
import axios from "axios";
import MarkdownIt from "markdown-it";
import emoji from "markdown-it-emoji";
import anchor from "markdown-it-anchor";
import spinner from "@/components/spinner.md";
import string from "string";

const opt = {
  slugify: (s) => string(s).slugify().toString(),
  permalink: true,
};

const markDownIt = new MarkdownIt({ html: true }).use(emoji).use(anchor, opt);

export default {
  name: "post",
  props: ["section", "id"],
  metaInfo() {
    return {
      title: this.title,
    };
  },

  data() {
    return {
      templateRender: null,
      title: "",
    };
  },
  render(createElement) {
    if (this.templateRender) {
      return this.templateRender();
    } else {
      return createElement(spinner);
    }
  },

  beforeRouteUpdate() {
    document.location.reload();
  },

  methods: {
    hasHistory() {
      return window.history?.length > 2;
    },
  },

  created() {
    const compilePost = async () => {
      // Fetch current post md

      let item = this.$store.state.postsIndex.filter((p) => p.id === this.id);

      if (!item || !item.length) {
        const compiled = VueWithCompiler.compile(`
        <div class="mt-5 fl-container">
          <div class="row w-100">
            <div class="col-sm-4 text-center mb-3 pt-3">
              <img src="/data/assets/not-found.svg" class="not-found-svg" />
            </div>
            <div class="col-sm-7 offset-sm-1 mb-3 pt-3">
            <h3 class="text-dark mb-4">No encontramos el recurso solicitado.</h3>
            <p>Quizá el enlace que te pasaron es viejo, intenta con uno diferente.</p>
            <hr />
            <p class="text-secondary">Si querías encontrarte con esta página, entonces... ¡Felicidades! la encontraste.</p>
            </div>
          </div>
        </div>
        `);
        this.templateRender = compiled.render;
        this.$options.staticRenderFns = [];
        for (const staticRenderFunction of compiled.staticRenderFns) {
          this.$options.staticRenderFns.push(staticRenderFunction);
        }
        return;
      }

      this.title = item[0].title;

      const url = "/" + item[0].url;

      const md = (await axios.get(url)).data;

      // MarkDown to HTML
      const html = markDownIt.render(md);

      const compiled = VueWithCompiler.compile(`
        <div class="post bg-white p-5 border shadow rounded">
          <div class="markdown-body">
            ${html}
          </div>
          <hr />
          <p class='text-center text-primary'>Desde TecPyme mandamos saludos a usted lector 🎉 esperemos que le haya gustado este artículo. ¡Hasta la próxima! 😄</p>
          <p class='display-1 text-center mb-3' style='font-size:20px'>¿Este artículo te fue útil? Dinos en los comentarios!</p>
          <component is="script" src="https://utteranc.es/client.js" repo="IvySoftwareMX/IvySoftwareBlog" issue-term="pathname" label="comment" theme="github-light" crossorigin="anonymous" async />
        </div>
      `);
      this.templateRender = compiled.render;
      this.$options.staticRenderFns = [];
      for (const staticRenderFunction of compiled.staticRenderFns) {
        this.$options.staticRenderFns.push(staticRenderFunction);
      }
      setTimeout(() => {
        if (!this.$route.hash) return;
        var element = document.querySelector(this.$route.hash);
        element.scrollIntoView({ behavior: "smooth", block: "start" });
      }, 150);
    };

    // console.log(compilePost);
    compilePost();
  },
};
</script>

<style scoped>
.not-found-svg {
  max-height: 30vh;
}

.header-anchor {
  opacity: 0;
}
*:hover > .header-anchor {
  opacity: 1;
}
</style>