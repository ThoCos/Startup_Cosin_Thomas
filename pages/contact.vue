<script setup>
const query = gql`
  query contacts {
    contact(where: { slug: "contact" }) {
      slug
      nom
      adresse
      telephone
    }
  }
`;

const contact = ref();
const { data } = await useAsyncQuery(query);
console.log(data.value);
contact.value = data.value.contact;
</script>
<template>
  <div class="text-white">
    <h2 class="text-3xl flex justify-start">{{ contact.nom }}</h2>
    <div>{{ contact.adresse }}</div>
    <div>{{ contact.telephone }}</div>
    <div>{{ contact.carte }}</div>
  </div>
</template>
