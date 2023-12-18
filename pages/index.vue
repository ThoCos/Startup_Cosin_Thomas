<script setup>
const query = gql`
  query PageAccueil {
    page(where: { slug: "accueil" }) {
      id
      slug
      titre
      texte {
        html
      }
    }
  }
`;

const contenuAccueil = ref();
const { data } = await useAsyncQuery(query);
console.log(data.value);
contenuAccueil.value = data.value.page;
</script>

<template>
  <div class="max-w-3xl space-y-4 mx-auto text-white">
    <h2 class="">{{ contenuAccueil.titre }}</h2>
    <div v-html="contenuAccueil.texte.html"></div>
  </div>
</template>
