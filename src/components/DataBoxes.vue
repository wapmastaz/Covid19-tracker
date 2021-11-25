<template>
  <div class="grid md:grid-cols-2 gap-4">

    <!-- box 1 -->
    <div class="bg-blue-100 text-center shadow-md rounded-md p-5">
      <h2 class="font-bold text-2xl mb-5 text-blue-900">Cases</h2>
        <div class="text-center mb-1">
          <span class="font-bold mr-2">New:</span>
          <span class="font-bold">{{formatNumber(stats.NewConfirmed)}}</span>
        </div>
        <div class="text-center">
          <span class="font-bold mr-2">Total:</span>
          <span class="font-bold">{{formatNumber(stats.TotalConfirmed)}}</span>
        </div>
    </div>

    <!-- box 2 -->
    <div class="bg-blue-200 text-center shadow-md rounded-md p-5">
      <h2 class="font-bold text-2xl mb-5 text-blue-900">Deaths</h2>
        <div class="text-center mb-1">
          <span class="font-bold mr-2">New:</span>
          <span class="font-bold">{{formatNumber(stats.NewDeaths)}}</span>
        </div>
        <div class="text-center">
          <span class="font-bold mr-2">Total:</span>
          <span class="font-bold">{{formatNumber(stats.TotalDeaths)}}</span>
        </div>
    </div>
    
  </div>
</template>

<script>
export default {
  props: {
    stats: {
      Object
    }
  },
  methods: {
    formatNumber(x) {
      return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    }
  },
}
</script>