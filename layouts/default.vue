<template>
  <div class="min-h-screen bg-gray-800">
    <nav
      class="container mx-auto flex justify-between items-center h-24 mb-10 text-white text-xl pl-10 border-b-[3px] border-teal-400"
    >
      <NuxtLink to="/">
        <h1 class="">Startup</h1>
      </NuxtLink>
      <div class="space-x-10 text-xl pr-10">
        <NuxtLink :to="'/produits'" class="hover:text-teal-400"
          >Produits</NuxtLink
        >
        <NuxtLink :to="'/articles'" class="hover:text-teal-400"
          >Articles</NuxtLink
        >
        <NuxtLink :to="'/entreprise'" class="hover:text-teal-400"
          >L'entreprise</NuxtLink
        >
        <NuxtLink :to="'/contact'" class="hover:text-teal-400"
          >Contact</NuxtLink
        >
      </div>
    </nav>
    <div class="container mx-auto px-3">
      <slot />
    </div>
  </div>
</template>
