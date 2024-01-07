<script setup>
const query = gql`
  query Produit($slug: String!) {
    produit(where: { slug: $slug }) {
      titre
      description {
        html
      }
      image {
        url
      }
    }
  }
`;

const produit = ref();
const route = useRoute();
const { data } = await useAsyncQuery(query, {
  slug: route.params.slug,
});
console.log(data.value);
produit.value = data.value.produit;
</script>

<template>
  <div v-if="produit" class="max-w-xl space-y-8 mx-auto text-white pb-10">
    <div class="flex justify-center">
      <NuxtImg
        class="rounded-lg w-[400px]"
        :src="produit.image.url"
        :alt="produit.titre"
      />
    </div>
    <h2 class="text-4xl text-[#A10909] font-bold">
      {{ produit.titre }}
    </h2>
    <div v-html="produit.description.html"></div>
  </div>
</template>
