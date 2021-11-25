<template>
  <div class="mt-6">
    <select @change="changeCountryData()" v-model="selected" class="form-select focus:outline-none border p-2 w-full rounded">
      <option value="0">Select Country</option>
      <option v-for="country in countries" :value="country.ID" :key="country.ID">
        {{country.Country}}
      </option>
    </select>
  </div>
</template>


<script>
export default {
  props: {
    countries: {
      Array
    }
  },
  data() {
    return {
      selected: 0
    }
  },
  methods: {
    changeCountryData() {
      const country = this.countries.find((item) => item.ID === this.selected);

      this.$emit('get-country', country)

    }
  },
}
</script>