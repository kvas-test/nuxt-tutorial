<template>
  <div class="section">
    <main class="container">
      <div class="columns is-multiline">
        <div v-for="article in articles" :key="article.id" class="column is-3">
          <Card :article="article" />
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import Card from '~/components/Card'

export default {
  name: 'HomePage',
  components: {
    Card
  },
  data() {
    return {
      articles: []
    }
  },
  created() {
    const files = require.context('~/articles', false, /.md$/)
    this.articles = files.keys().map((filename) => {
      const key = filename.replace('./', '').replace('.md', '')
      const { attributes } = require(`~/articles/${key}.md`)

      return {
        id: key,
        slug: key,
        imgURL: attributes.imgURL,
        uploadAt: attributes.uploadAt,
        author: attributes.author,
        title: attributes.title,
        desc: attributes.desc
      }
    })
  }
}
</script>
