<template>
  <div>
    <div class="flex justify-between flex-wrap px-5 sm:px-10 xl:px-0">
      <h1 class="text-2xl md:text-3xl mb-6 text-theme-text-primary"><slot></slot></h1>
      <div class="hidden sm:flex items-center text-theme-text-tertiary text-2xs px-3 sm:px-8 xl:px-6 py-3 mb-6 bg-stat-background rounded-md">
        <div class="pr-6">Height: {{ height.toLocaleString() }}</div>
        <div class="pr-6">Network: {{ alias }}</div>
        <div class="pr-6">Supply: {{ readableCrypto(supply) }}</div>
        <div>Market Cap: <currency :amount="+supply"></currency></div>
      </div>
    </div>
    <div class="sm:hidden flex items-center justify-between text-theme-text-tertiary text-2xs px-5 sm:px-8 xl:px-6 py-3 bg-stat-background">
      <div class="mr-2">
        <span>Height:</span>
        <span class="block md:inline-block">{{ height.toLocaleString() }}</span>
      </div>
      <div class="mr-2">
        <span>ARK/{{name}}:</span>
        <span class="block md:inline-block">{{ rawCurrency(rate, name) }}</span>
      </div>
      <div>
        <span>Supply:</span>
        <span class="block md:inline-block">{{ readableCrypto(supply) }}</span>
      </div>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
import { mapGetters } from 'vuex'

export default {
  computed: {
    ...mapGetters('network', ['alias', 'supply', 'height']),
    ...mapGetters('currency', ['name', 'rate', 'symbol']),
  },
}
</script>