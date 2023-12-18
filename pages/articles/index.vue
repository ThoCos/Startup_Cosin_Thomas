<script setup>
const query = gql`
  query articles {
    articles {
      titre
      image {
        url
      }
      texte {
        html
      }
      slug
    }
  }
`;

const articles = ref();
const { data } = await useAsyncQuery(query);
console.log(data.value);
articles.value = data.value.articles;
</script>

<template>
  <ul
    v-if="articles"
    class="grid gap-8 grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 2xl:grid-cols-6 pb-10"
  >
    <li
      v-for="article in articles"
      :key="article.titre"
      class="bg-gray-300 shadow-md flex justify-center items-center p-3 rounded-lg transition-transform transform hover:scale-110"
    >
      <NuxtLink :to="`articles/${article.slug}`">
        <NuxtImg
          :src="article.image.url"
          :alt="article.titre"
          class="rounded-lg"
        />
        <h2 class="text-3xl flex justify-start">{{ article.titre }}</h2>
      </NuxtLink>
    </li>
  </ul>
</template>
