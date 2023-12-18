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
    <h2 class="text-3xl flex justify-start">{{ entreprise.nom }}</h2>
    <div>{{ entreprise.historique }}</div>
    <div>{{ entreprise.missions }}</div>
  </di>
</template>
