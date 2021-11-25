<template>
  <div class="text-center">
    <h2 class="text-3xl font-bold sm:text-2xl">{{title}}</h2>
    <div class="mt-2 mb-10 font-bold text-gray-600">{{titmestamp}}</div>
  </div>
</template>

<script>
import moment from 'moment'
export default {
  props: {
    title: {
      String
    },
    dataDate: {
      
    }
  },

  computed:{
    titmestamp: function() {
      return moment(this.dataDate).format('MMMM Do YYYY, h:mm:ss a')
    }
  }
}
</script>