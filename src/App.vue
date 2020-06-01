<template>
  <div id="app" :class="currentMarqueeBackground">
    <header>
      <section>
        <img src="@/assets/abc_logo.svg"/>
        <nav>
          <a :click="updateMarqueeBody('Industries')">Industries</a>
          <a :click="updateMarqueeBody('Services')">Services</a>
          <a :click="updateMarqueeBody('About Us')">About Us</a>
        </nav>
      </section>
      <button>
        Contact Us
      </button>
    </header>
    <MarqueeBody v-bind="currentMarqueeBody"></MarqueeBody>
  </div>
</template>

<script>
import MarqueeBody from "./components/MarqueeBody.vue";

import { pages } from "@/assets/content.json";

export default {
  // name: "App",
  components: {
    MarqueeBody 
  },
  data() {
    return {
      marqueeList: pages,
      currentMarqueeBody: pages[0]
    }
  },
  methods: {
    updateMarqueeBody: function(title) {
      // console.log(this.marqueeList);
      console.log(title);
      const correctBody = this.marqueeList.forEach(item => console.log(item.title));
      console.log(correctBody);
    },
  },
  mounted() {
    // console.log(this.currentMarqueeBody);
  },
  computed: {
    currentMarqueeBackground: function() {
      return this.currentMarqueeBody.title.toLowerCase();
    } 
  }
};
</script>

<style lang="scss">
body {
  margin: 0;
}
#app {
  // -webkit-font-smoothing: antialiased;
  // -moz-osx-font-smoothing: grayscale;
  font-family: Helvetica, Arial, sans-serif;
  min-height: 100vh;
  color: #fff;
  padding: 10px;
  background-size: cover;

  &.industries {
    background: url("./assets/slide_one.jpg") no-repeat center center;
  }
  &.services {
    background: url("./assets/slide_two.jpg") no-repeat center center;
  }
  &.contact-us {
    background: url("./assets/slide_three.jpg") no-repeat center center;
  }
}
</style>
