<template>
  <div>
    <div class="uk-section">
      <div class="uk-container uk-container-large">
        <h1>Nekoka Fun Blog</h1>
        <Articles :atricle="articles"></Articles>
      </div>
    </div>
  </div>
</template>

<script>
import articlesQuery from '~/apollo/queries/article/articles'
import Articles from '~/components/Articles'

export default {
  components: {
    Articles
  },
  data() {
    return {
      articles: []
    }
  },
  apollo: {
    articles: {
      prefetch: true,
      query: articlesQuery,
      variables() {
        return { id: parseInt(this.$route.params.id) }
      }
    }
  }
}
</script>
