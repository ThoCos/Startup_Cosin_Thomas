<script setup>
const query = gql`
  query Produits {
    produits {
      titre
      image {
        url
      }
      description {
        html
      }
      slug
    }
  }
`;

const contenuProduits = ref();
const { data } = await useAsyncQuery(query);
console.log(data.value);
contenuProduits.value = data.value.produits;
</script>

<template>
  v-for="produit in produits" :key="produits.titre"

  <h2 class="">{{ contenuProduits.titre }}</h2>
  <div v-html="contenuProduits.description.html"></div>
</template>
