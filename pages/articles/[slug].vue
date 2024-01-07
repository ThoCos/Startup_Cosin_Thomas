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
  <div v-if="article" class="max-w-xl space-y-4 mx-auto pb-10 text-white">
    <div class="flex justify-center">
      <NuxtImg
        class="rounded-lg w-[400px]"
        :src="article.image.url"
        :alt="article.titre"
      />
    </div>
    <div>
      <h2 class="text-3xl mb-4 text-[#A10909] font-bold">
        {{ article.titre }}
      </h2>
    </div>
    <div v-html="article.texte.html"></div>
  </div>
</template>
