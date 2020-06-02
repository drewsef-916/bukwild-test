<template>
  <div class="layout layout-default">
    <slot>
      <header>
        <section>
          <img class="logo" src="@/assets/abc_logo.svg"/>
          <nav>
            <a class="nav-item" v-on:click="updateMarqueeBody('Industries')">Industries</a>
            <a class="nav-item" v-on:click="updateMarqueeBody('Services')">Services</a>
            <a class="nav-item" v-on:click="updateMarqueeBody('About Us')">About Us</a>
          </nav>
        </section>
        <button class="contact">Contact Us</button>
      </header>
    </slot>
  </div>
</template>

<script>
export default {
  methods: {
    updateMarqueeBody: function(title) {
      this.$emit('updateMarqueeBody', title);
    }
  }
};
</script>

<style lang="scss">
@import "@/scss/mixins.scss";

header {
  padding: 1rem 0;
  display: flex;
  justify-content: space-between;
}
a, button {
  cursor: pointer;
}
a {
  @include onHover(#fff, #ffc001);
}
button {
  font-size: calc(14px + 0.1vw);
}
.layout {
  @include responsive(width, 300px, 80%, 1440px);
  margin: 0 auto;
}
.logo {
  padding: 0 0 1rem;
}
.nav-item {
  display: block;
  padding: 10% 0;
}
.contact {
  height: 3rem;
  min-height: 2rem;
  padding: 0.5rem 1.5rem;
  background-color: transparent;
  color: #fff;
  border: 1px solid #fff;
}
</style>
