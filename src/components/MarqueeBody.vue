<template>
  <main>
    <section class="headings">
      <h1>{{headline}}</h1>
      <h3>{{subhead}}</h3>
    </section>
    <section class="cta">
      <span>{{cta}}</span>
      <div class="lets-talk">
        <span>Let's Talk</span>
        <font-awesome-icon class="icon arrow" icon="long-arrow-alt-right" />
      </div>
    </section>
  </main>
</template>

<script>
export default {
  props: ["blocks"],
  data: function() {
    return {
      headline: this.blocks[0].headline,
      subhead: this.blocks[0].subhead,
      cta: this.blocks[0].cta
    };
  },
  watch: {
    blocks: {
      immediate: true,
      handler([newProps]) {
        this.headline = newProps.headline;
        this.subhead = newProps.subhead;
        this.cta = newProps.cta;
      }
    }
  }
};
</script>

<style lang="scss">
@import "@/scss/mixins.scss";

main {
  @include responsive(width, 300px, 80%, 1440px);
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  margin: 0 auto;
}
.headline, .subheadline {
  color: #fff
}
.headings {
  @include responsive(height, 46vh, auto, none);
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  margin-bottom: 2rem;

  h1, h3 {
    @include responsive(width, 300px, 50%, 50%);
  }
  h1 {
    font-size: calc(42px + 0.2vw);
  }
  h3 {
    font-size: calc(12px + 0.2vw);
    font-weight: 300;
  }
}
.cta {
  @include responsive(height, 120px, 25vh, 200px);
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  align-items: center;
  padding: 0 0.5rem;
  background-color: #fff;
  color: #000;

  > span {
    font-weight: 600;
    text-align: center;
  }
}
.lets-talk {
  font-size: calc(10px + 0.2vw);
  text-transform: uppercase;
  display: flex;
  align-items: center;

  > span {
    padding: 0.5rem 1rem;
  }
}
.icon {
  color: #ffc001;
  font-size: 1.5rem;
}
</style>
