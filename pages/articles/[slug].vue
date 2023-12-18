<script setup>
const query = gql`
  query article($slug: String!) {
    article(where: { slug: $slug }) {
      titre
      texte {
        html
      }
      image {
        url
      }
    }
  }
`;

const article = ref();
const route = useRoute();
const { data } = await useAsyncQuery(query, {
  slug: route.params.slug,
});
console.log(data.value);
article.value = data.value.article;
</script>

<template>
  <div v-if="article" class="max-w-lg space-y-8 mx-auto pb-10 text-white">
    <NuxtImg class="rounded-lg" :src="article.image.url" :alt="article.titre" />
    <div class="">
      <h2 class="text-3xl mb-3">
        {{ article.titre }}
      </h2>
    </div>
    <div v-html="article.texte.html"></div>
  </div>
</template>
