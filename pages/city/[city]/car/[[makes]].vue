<template>
 <div>
    <CarCards v-if="cars.length" :cars="cars" />
    <h1 v-else class="text-red-600">No Cars Found With Filters</h1>
</div>
</template>

<script lang="ts" setup>
const route = useRoute();
const {data:cars, refresh}= await useFetchCars(route.params.city, {
  minPrice: route.query.minPrice,
  maxPrice: route.query.maxPrice,
  make: route.params.makes,
  
});
// console.log(route.params.makes.toLowerCase());

watch(
  () => route.query,
  () => {
    window.location.reload(true);
  }
);
</script>

<style>

</style>