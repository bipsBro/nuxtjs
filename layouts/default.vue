<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-12">
        <ul class="uk-navbar-nav">
          <li>
            <router-link to="/" tag="a">Home </router-link>
          </li>
          <li v-for="category in categories">
            <router-link
              :to="{ name: 'categories-id', params: { id: category.id } }"
              tag="a"
              >{{ category.name }}
            </router-link>
          </li>
        </ul>
      </div>
    </div>
    <nuxt />
  </div>
</template>
<script>
import categoriesQuery from "~/apollo/queries/category/categories";

export default {
  data() {
    return {
      categories: []
    };
  },
  apollo: {
    categories: {
      prefetch: true,
      query: categoriesQuery
    }
  }
};
</script>
