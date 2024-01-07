<template>
  <div class="min-h-screen bg-gradient-to-b from-gray-400 to-gray-600">
    <nav
      class="container mx-auto flex justify-between items-center h-24 mb-10 text-white text-xl pl-10 border-b-[3px] border-[#A10909]"
    >
      <NuxtLink to="/">
        <h1 class="w-[60%] mt-3"><img src="public/logo.png" /></h1>
      </NuxtLink>
      <div class="space-x-10 text-xl pr-10">
        <NuxtLink :to="'/produits'" class="hover:text-[#A10909]"
          >Voitures</NuxtLink
        >
        <NuxtLink :to="'/articles'" class="hover:text-[#A10909]"
          >Actualités</NuxtLink
        >
        <NuxtLink :to="'/entreprise'" class="hover:text-[#A10909]"
          >L'entreprise</NuxtLink
        >
        <NuxtLink :to="'/contact'" class="hover:text-[#A10909]"
          >Contact</NuxtLink
        >
      </div>
    </nav>
    <div class="container mx-auto px-3">
      <slot />
    </div>
  </div>
</template>
