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
  <div class="text-white leading-10 mt-[100px]">
    <h2 class="text-5xl flex text-[#A10909] mb-4 font-bold justify-center">
      {{ contact.nom }}
    </h2>
    <div class="flex justify-center text-2xl">{{ contact.adresse }}</div>
    <div class="flex justify-center text-2xl">{{ contact.telephone }}</div>
    <div>{{ contact.carte }}</div>
    <div class="flex justify-center py-10">
      <iframe
        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d1263.0727615109208!2d4.607149646692893!3d50.71723934768839!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x47c17d7411704eef%3A0x30bbaf4d6d8a913b!2sRue%20de%20la%20Limite%206%2C%201300%20Wavre!5e0!3m2!1sfr!2sbe!4v1704580844100!5m2!1sfr!2sbe"
        width="600"
        height="450"
        style="border: 0"
        allowfullscreen=""
        loading="lazy"
        referrerpolicy="no-referrer-when-downgrade"
        class="rounded-lg"
      ></iframe>
    </div>
  </div>
</template>
