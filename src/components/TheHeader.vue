<template>
  <header>
    <center-wrapper :top="true">
      <div class="leadin">A video archive of</div>
      <h1>Police Abuses</h1>
      <div class="leadout">{{ total }} Videos</div>
      <incident-filter :value="city" :options="allCities" />
    </center-wrapper>
  </header>
</template>

<script>
import { computed } from '@vue/composition-api'

import CenterWrapper from '@/components/CenterWrapper.vue'
import useIncidents from '@/use/incidents'
import IncidentFilter from '@/components/IncidentFilter.vue'

export default {
  components: {
    CenterWrapper,
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

<style scoped lang="postcss">
header {
  @mixin color-negative;

  position: sticky;
  top: 0;
  padding: 0.5em 0 2em;
  z-index: var(--z-header);
  border-bottom: 1px solid var(--color-white);
}
.leadin {
  font-size: 1.125em;
  line-height: 1;
}
.leadout {
  font-size: 0.875em;
  line-height: 1;
  text-transform: uppercase;
}
</style>
