<script setup>
const query = gql`
  query entreprises {
    entreprise(where: { slug: "entreprise" }) {
      slug
      nom
      historique
      missions
    }
  }
`;

const entreprise = ref();
const { data } = await useAsyncQuery(query);
console.log(data.value);
entreprise.value = data.value.entreprise;
</script>
<template>
  <di class="text-white">
    <h2 class="text-3xl flex justify-center mb-5">{{ entreprise.nom }}</h2>
    <h2 class="text-3xl mb-2">Notre histoire</h2>
    <div>{{ entreprise.historique }}</div>
    <h2 class="text-3xl mb-2 mt-5">Nos missions</h2>
    <div>{{ entreprise.missions }}</div>
  </di>
</template>
