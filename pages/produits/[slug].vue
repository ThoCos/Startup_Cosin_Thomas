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
  <div v-if="produit" class="max-w-lg space-y-8 mx-auto">
    <div class="flex">
      <NuxtImg
        class="rounded-lg w-[300px]"
        :src="produit.image.url"
        :alt="produit.titre"
      />
      <div class="flex flex-col m-4">
        <h2
          class="text-3xl text-center flex flex-col items-center justify-center bg-indigo-200 p-3 rounded-lg mt-2"
        >
          <div class="mx-3 mb-1">
            {{ produit.titre }}
          </div>
        </h2>
      </div>
    </div>
    <p class="text-justify pb-20">{{ produit.description.html }}</p>
  </div>
</template>
