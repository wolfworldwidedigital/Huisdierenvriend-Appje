<script lang="ts" setup>
const { data } = await useAsyncGql('getProductCategories', { first: 6 });
const productCategories = data.value?.productCategories?.nodes || [];

useSeoMeta({
  title: `Home`,
  ogTitle: `Huisdierenvriend`,
  description: `Huisdierenvriend biedt de ultieme verzorging voor je huisdier. Van innovatieve speeltjes en gezonde voeding tot comfortabele slaapplekken, onze producten zijn speciaal ontworpen om het leven van jouw trouwe viervoeter te verrijken.`,
  ogDescription: `Huisdierenvriend biedt de ultieme verzorging voor je huisdier. Van innovatieve speeltjes en gezonde voeding tot comfortabele slaapplekken, onze producten zijn speciaal ontworpen om het leven van jouw trouwe viervoeter te verrijken.`,
  ogImage: `https://user-images.githubusercontent.com/5116925/218879668-f4c1f9fd-bef4-44b0-bc7f-e87d994aa3a1.png`,
  twitterCard: `summary_large_image`,
});
</script>

<template>
  <main>
    <HeroBanner />

    <div class="container flex flex-wrap items-center justify-center my-16 text-center gap-x-8 gap-y-4 brand lg:justify-between">
      <NuxtImg src="/images/logoipsum-211.svg" alt="Brand 1" width="132" height="35" />
      <NuxtImg src="/images/logoipsum-221.svg" alt="Brand 2" width="119" height="30" />
      <NuxtImg src="/images/logoipsum-225.svg" alt="Brand 3" width="49" height="48" />
      <NuxtImg src="/images/logoipsum-280.svg" alt="Brand 4" width="78" height="30" />
      <NuxtImg src="/images/logoipsum-284.svg" alt="Brand 5" width="70" height="44" />
      <NuxtImg src="/images/logoipsum-215.svg" alt="Brand 6" width="132" height="40" />
    </div>

    <section class="container my-16">
      <div class="flex items-end justify-between">
        <h2 class="text-lg font-semibold md:text-2xl">{{ $t('messages.shop.shopByCategory') }}</h2>
        <NuxtLink class="text-primary" to="/categories">{{ $t('messages.general.viewAll') }}</NuxtLink>
      </div>
      <div class="grid justify-center grid-cols-2 gap-4 mt-8 md:grid-cols-3 lg:grid-cols-6">
        <CategoryCard v-for="(category, i) in productCategories" :key="i" class="w-full" :node="category" />
      </div>
    </section>

    <section class="container grid gap-4 my-24 md:grid-cols-2 lg:grid-cols-4">
      <div class="flex items-center gap-8 p-8 bg-white rounded-lg">
        <NuxtImg src="/icons/box.svg" width="60" height="60" alt="Gratis verzending" loading="lazy" />
        <div>
          <h3 class="text-xl font-semibold">Gratis verzending</h3>
          <p class="text-sm">Gratis verzending bij een bestelling van meer dan €50</p>
        </div>
      </div>
      <div class="flex items-center gap-8 p-8 bg-white rounded-lg">
        <NuxtImg src="/icons/moneyback.svg" width="60" height="60" alt="Geld terug" loading="lazy" />
        <div>
          <h3 class="text-xl font-semibold">Gemoedsrust</h3>
          <p class="text-sm">30 dagen geld-terug-garantie</p>
        </div>
      </div>
      <div class="flex items-center gap-8 p-8 bg-white rounded-lg">
        <NuxtImg src="/icons/secure.svg" width="60" height="60" alt="Veilige betaling" loading="lazy" />
        <div>
          <h3 class="text-xl font-semibold">100% veilige betaling</h3>
          <p class="text-sm">Your payment are safe with us.</p>
        </div>
      </div>
      <div class="flex items-center gap-8 p-8 bg-white rounded-lg">
        <NuxtImg src="/icons/support.svg" width="60" height="60" alt="Helpdesk 24/7" loading="lazy" />
        <div>
          <h3 class="text-xl font-semibold">Ondersteuning 24/7</h3>
          <p class="text-sm">24/7 online ondersteuning</p>
        </div>
      </div>
    </section>
  </main>
</template>

<style scoped>
.brand img {
  max-height: min(8vw, 120px);
  object-fit: contain;
  object-position: center;
}
</style>
