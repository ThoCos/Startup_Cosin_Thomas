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
  <div class="text-white mx-10 pb-10">
    <h2 class="text-3xl flex justify-center mb-10">{{ entreprise.nom }}</h2>
    <h2 class="text-3xl text-[#A10909] font-bold mb-5">Notre histoire</h2>
    <div>{{ entreprise.historique }}</div>
    <h2 class="text-3xl text-[#A10909] font-bold mb-5 mt-5">Nos missions</h2>
    <div>{{ entreprise.missions }}</div>
  </div>
</template>
