<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-12">
        <ul class="nav">
          <li class="nav-item">
            <router-link
              to="/"
              class="nav-link active"
              aria-current="page"
              tag="a"
              >Home
            </router-link>
          </li>
          <li class="nav-item" v-for="category in categories">
            <router-link
              :to="{ name: 'categories-id', params: { id: category.id } }"
              tag="a"
              class="nav-link"
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
