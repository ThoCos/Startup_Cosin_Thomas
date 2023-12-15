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
    class="grid gap-8 grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 2xl:grid-cols-6 pb-10"
  >
    <li
      v-for="produit in produits"
      :key="produit.titre"
      class="bg-gray-300 shadow-md flex justify-center items-center p-3 rounded-lg transition-transform transform hover:scale-110"
    >
      <NuxtLink :to="`produits/${produit.slug}`">
        <NuxtImg
          :src="produit.image.url"
          :alt="produit.titre"
          class="rounded-lg"
        />
        <h2 class="text-3xl flex justify-start">{{ produit.titre }}</h2>
      </NuxtLink>
    </li>
    <li
      class="bg-gray-300 shadow-md flex flex-col justify-center items-center p-3 rounded-lg transition-transform transform hover:scale-110"
    >
      <div
        class="bg-gray-400 w-[150px] h-[130px] rounded-lg mt-[-5px] animate-pulse flex justify-center items-center cursor-pointer"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 24 24"
          class="animate-spin w-[100px] text-gray-300 fill-current"
        >
          <path
            d="M12 3C16.9706 3 21 7.02944 21 12H19C19 8.13401 15.866 5 12 5V3Z"
          ></path>
        </svg>
      </div>
      <div
        class="bg-gray-400 rounded-lg w-[150px] h-8 mt-[10px] animate-pulse cursor-pointer"
      ></div>
      <div
        class="bg-gray-400 rounded-lg w-[150px] h-6 mt-3 animate-pulse cursor-pointer"
      ></div>
    </li>
  </ul>
</template>
