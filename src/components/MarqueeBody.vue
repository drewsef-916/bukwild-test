<template>
  <main>
    <section>
      <div class="headline">
        <span>{{title}}</span>
      </div>
      <div class="subheadline">
      </div>
    </section>
  </main>
</template>

<script>

export default {
  props: ["title", "slug", "blocks"],
  data: function() {
    return {
      type: this.blocks[0].type,
      headline: this.blocks[0].headline,
      subhead: this.blocks[0].subhead,
      cta: this.blocks[0].cta,
      background: this.blocks[0].background
    };
  },
};
</script>

<style lang="scss">
  .headline, .subheadline {
    color: #333
  }
</style>
