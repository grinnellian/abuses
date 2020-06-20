<template>
  <the-header>
    <incident-filter :value="city" :options="allCities" />
  </the-header>
</template>

<script>
import { computed } from '@vue/composition-api'

import useIncidents from '@/use/incidents'
import TheHeader from '@/components/TheHeader.vue'
import IncidentFilter from '@/components/IncidentFilter.vue'

export default {
  components: {
    TheHeader,
    IncidentFilter,
  },

  props: {
    city: {
      type: String,
      default: '',
    },
  },

  setup() {
    const { list, total } = useIncidents()

    const allCities = computed(() => [...new Set([...list.value.map((i) => i.city)])].sort())

    return { total, allCities }
  },
}
</script>
