<template>
  <div>
    <Header />

    <section class="main-content columns">
      <div class="container column is-10">
        <nuxt />
      </div>
    </section>

    <Footer />
  </div>
</template>

<script>
import Header from '~/components/Header'
import Footer from '~/components/Footer'

export default {
  components: {
    Header,
    Footer
  }
}
</script>
