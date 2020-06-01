<template>
  <div id="app" :class="currentMarqueeBackground">
    <header>
      <section>
        <img class="logo" src="@/assets/abc_logo.svg"/>
        <nav>
          <a class="nav-item" v-on:click="updateMarqueeBody('Industries')">Industries</a>
          <a class="nav-item" v-on:click="updateMarqueeBody('Services')">Services</a>
          <a class="nav-item" v-on:click="updateMarqueeBody('About Us')">About Us</a>
        </nav>
      </section>
      <button class="contact">
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
      currentMarqueeBody: {}
    }
  },
  methods: {
    updateMarqueeBody: function(title) {
      const [marqueeBody] = this.marqueeList.filter(item => item.title === title);
      this.currentMarqueeBody = marqueeBody;
      console.log(this.currentMarqueeBody);
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
  margin: 0;
}
header {
  display: flex;
  justify-content: space-between;
}
a, button {
  cursor: pointer;
}
#app {
  // -webkit-font-smoothing: antialiased;
  // -moz-osx-font-smoothing: grayscale;
  font-family: Helvetica, Arial, sans-serif;
  min-height: 100vh;
  color: #fff;
  padding: 10px;

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
.nav-item {
  display: block;
  padding: 10% 0;
}
.contact {
  height: 2rem;
  min-height: 2rem;
  padding: .5rem 1rem;
  background-color: transparent;
  color: #fff;
  border: 1px solid #fff;
}
</style>
