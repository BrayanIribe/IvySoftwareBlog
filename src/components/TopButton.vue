<template>
  <div class="top-bt">
    <transition name="fade" mode="out-in">
      <button
        type="button"
        v-if="windowTop > 50"
        @click="goTop()"
        class="bg-primary text-white"
        style="border: none"
      >
        <img src="/data/assets/arrow-up.svg" class="fill-white" />
      </button>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      windowTop: 0,
    };
  },
  mounted() {
    window.addEventListener("scroll", this.onScroll);
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.onScroll);
  },
  methods: {
    onScroll() {
      this.windowTop =
        window.top.scrollY; /* or: e.target.documentElement.scrollTop */
    },
    goTop() {
      window.scrollTo(0, 0);
    },
  },
};
</script>

<style scoped>
.top-bt {
  position: sticky;
  bottom: 80px;
  border: 0px;
}

.top-bt > button {
  float: right;
  margin-right: 25px;
  width: 70px;
  height: 70px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 70px;
  outline: none;
}

.top-bt > button > img {
  width: 35px;
  height: 35px;
  filter: invert(1);
}
</style>