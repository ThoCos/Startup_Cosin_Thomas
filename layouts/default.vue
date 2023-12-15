<template>
  <div class="min-h-screen bg-teal-300">
    <nav
      class="container mx-auto px-3 h-24 flex items-center justify-center mb-10"
    >
      <NuxtLink to="/">
        <h1 class="text-5xl">Startup</h1>
      </NuxtLink>
      <NuxtLink :to="'/produits'">Produits</NuxtLink>
    </nav>
    <div class="container mx-auto px-3">
      <slot />
    </div>
  </div>
</template>
