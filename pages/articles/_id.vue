<template>
  <div>
    <div
      v-if="article.image"
      id="banner"
      class=""
      :data-src="api_url + article.image.url"
      uk-img
    >
      <h1>{{ article.title }}</h1>
    </div>

    <div class="">
      <div class="">
        <div v-if="article.content" id="editor">{{ article.content }}</div>
        <p v-if="article.published_at">
          {{ moment(article.published_at).format("MMM Do YY") }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import articleQuery from "~/apollo/queries/article/article";
var moment = require("moment");

export default {
  data() {
    return {
      article: {},
      moment: moment,
      api_url: process.env.strapiBaseUri
    };
  },
  apollo: {
    article: {
      prefetch: true,
      query: articleQuery,
      variables() {
        return { id: parseInt(this.$route.params.id) };
      }
    }
  }
};
</script>
