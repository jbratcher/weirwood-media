<template>
  <v-layout>
    <v-col>
      <v-sheet class="ma-0" color="secondary darken-2" dark tile>
        <h1 class="headline pa-2" display="headline">Blog > {{ blogPost.title }}</h1>
      </v-sheet>
      <article>
        <v-card class="d-flex flex-column align-center mx-auto">
          <v-img
            src="https://picsum.photos/1280/920"
            lazy-src="https://picsum.photos/1280/920"
            width="1280"
            max-height="300"
          />
          <v-card-title>{{blogPost.title}}</v-card-title>
          <v-card-subtitle>{{blogPost.description}}</v-card-subtitle>
          <v-card-text v-html="$md.render(blogPost.body)"></v-card-text>
        </v-card>
      </article>
    </v-col>
  </v-layout>
</template>
<script>
export default {
  async asyncData({ params, payload }) {
    if (payload) return { blogPost: payload };
    else
      return {
        blogPost: await require(`~/assets/content/blog/${params.blog}.json`)
      };
  }
};
</script>
<style lang="scss" scoped>
.col {
  margin: 0;
  padding: 0;
}
.v-card__title {
  font-size: 2.33rem;
  font-weight: 700;
}
.v-card__subtitle {
  font-size: 1.25rem;
}
.v-card__text {
  font-size: 1rem;
}
@media screen and (min-width: 768px) {
  .v-card__title {
    font-size: 3rem;
    margin: 2rem 0;
  }
  .v-card__subtitle {
    font-size: 1.75rem;
  }
  .v-card__text {
    margin: 4rem;
    max-width: 70vw;
  }
}
</style>