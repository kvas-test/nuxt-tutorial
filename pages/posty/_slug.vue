<template>
  <section class="section content">
    <component :is="selectedArticle" />
  </section>
</template>

<script>
export default {
  name: 'Article',
  data() {
    return {
      selectedArticle: null
    }
  },
  created() {
    const markdown = require(`~/articles/${this.$route.params.slug}.md`)
    this.selectedArticle = markdown.vue.component
  }
}
</script>
