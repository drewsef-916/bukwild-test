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
  .headline, .subheadline {
    color: #fff
  }
  .headings {
    display: flex;

    h1, h3 {
      flex-basis: 50%;
    }
  }
  .cta {
    display: flex;
    justify-content: space-around;
    align-items: center;
    background-color: #fff;
    color: #000;
    width: 80%;
    margin: 0 auto;
  }
  .icon {
    color: #ffc001;
    font-size: 1.5rem;
  }
</style>
