<template>
  <div>
    <div class="uk-section">
      <div class="uk-container uk-container-large">
        <Articles :articles="articles"></Articles>
      </div>
    </div>
  </div>
</template>

<script>
import articlesQuery from "~/apollo/queries/article/articles";
import Articles from "~/components/Articles";

export default {
  data() {
    return {
      articles: []
    };
  },
  components: {
    Articles
  },
  apollo: {
    articles: {
      prefetch: true,
      query: articlesQuery
    }
  }
};
</script>
