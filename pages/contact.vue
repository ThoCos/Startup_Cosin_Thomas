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
  <div class="text-white leading-10 mt-[50px] bg-gray-600/25 rounded-md p-5">
    <h1 class="text-white text-2xl flex justify-center mb-5">
      Pour plus d'informations
      <span class="font-bold ml-2"> Contactez-nous</span>!
    </h1>
    <h2 class="text-5xl flex text-[#A10909] mb-4 font-bold justify-center">
      {{ contact.nom }}
    </h2>
    <div class="flex justify-center text-2xl">{{ contact.adresse }}</div>
    <div class="flex justify-center text-2xl">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        class="w-6 h-6 mr-2 mt-1"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M2.25 6.75c0 8.284 6.716 15 15 15h2.25a2.25 2.25 0 0 0 2.25-2.25v-1.372c0-.516-.351-.966-.852-1.091l-4.423-1.106c-.44-.11-.902.055-1.173.417l-.97 1.293c-.282.376-.769.542-1.21.38a12.035 12.035 0 0 1-7.143-7.143c-.162-.441.004-.928.38-1.21l1.293-.97c.363-.271.527-.734.417-1.173L6.963 3.102a1.125 1.125 0 0 0-1.091-.852H4.5A2.25 2.25 0 0 0 2.25 4.5v2.25Z"
        />
      </svg>

      {{ contact.telephone }}
    </div>
    <div>{{ contact.carte }}</div>
    <div class="flex justify-center py-10">
      <iframe
        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d1263.0727615109208!2d4.607149646692893!3d50.71723934768839!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x47c17d7411704eef%3A0x30bbaf4d6d8a913b!2sRue%20de%20la%20Limite%206%2C%201300%20Wavre!5e0!3m2!1sfr!2sbe!4v1704580844100!5m2!1sfr!2sbe"
        width="600"
        height="350"
        style="border: 0"
        allowfullscreen=""
        loading="lazy"
        referrerpolicy="no-referrer-when-downgrade"
        class="rounded-lg"
      ></iframe>
    </div>
  </div>
</template>
