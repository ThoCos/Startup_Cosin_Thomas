<script setup>
const query = gql`
  query Produits {
    produits {
      id
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

const produits = ref();
const { data } = await useAsyncQuery(query);
console.log(data.value);
produits.value = data.value.produits;
</script>

<template>
  <ul
    v-if="produits"
    class="grid gap-8 grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 2xl:grid-cols-6 pb-10 text-white"
  >
    <li
      v-for="produit in produits"
      :key="produit.titre"
      class="bg-[#A10909] shadow-md flex justify-center items-center p-3 rounded-lg transition-transform transform hover:scale-110"
    >
      <NuxtLink :to="`produits/${produit.slug}`">
        <NuxtImg
          :src="produit.image.url"
          :alt="produit.titre"
          class="rounded-lg"
        />
        <h2 class="text-2xl flex justify-center">{{ produit.titre }}</h2>
      </NuxtLink>
    </li>
  </ul>
</template>
