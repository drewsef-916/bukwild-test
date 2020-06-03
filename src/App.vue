<template>
  <div id="app" :class="currentMarqueeBackground">
    <DefaultLayout :marqueeList="marqueeList" @updateMarqueeBody="updateMarqueeBody"></DefaultLayout>
    <MarqueeBody v-bind="currentMarqueeBody"></MarqueeBody>
  </div>
</template>

<script>
import DefaultLayout from "./layouts/DefaultLayout.vue";
import MarqueeBody from "./components/MarqueeBody.vue";

import { pages } from "@/assets/content.json";

export default {
  components: {
    DefaultLayout,
    MarqueeBody
  },
  data() {
    return {
      marqueeList: pages,
      currentMarqueeBody: {}
    }
  },
  methods: {
    updateMarqueeBody: function(title) {
      const [marqueeBody] = this.marqueeList.filter(item => item.title === title);
      this.currentMarqueeBody = marqueeBody;
    }
  },
  created() {
    // set initial marquee body to the first option, industries, on render
    this.currentMarqueeBody = this.marqueeList[0];
  },
  computed: {
    currentMarqueeBackground: function() {
      return this.currentMarqueeBody.slug;
    }
  }
};
</script>

<style lang="scss">
html {
  font-size: 14px;
}
body {
  font-size: calc(14px + 0.2vw);
  margin: 0;
}
#app {
  font-family: Helvetica, Arial, sans-serif;
  min-height: 100vh;
  color: #fff;
  background-color: #222;
  padding: 0 10px;

  &.industries {
    background: url("./assets/slide_one.jpg") no-repeat center center;
    background-size: cover;
  }
  &.services {
    background: url("./assets/slide_two.jpg") no-repeat center center;
    background-size: cover;
  }
  &.about-us {
    background: url("./assets/slide_three.jpg") no-repeat center center;
    background-size: cover;
  }
}
</style>
