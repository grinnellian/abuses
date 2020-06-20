<template>
  <div id="app">
    <filter-header :city="city" />
    <incident-details />
    <incident-list :city="city" />
  </div>
</template>

<script>
import IncidentDetails from '@/components/IncidentDetails.vue'
import IncidentList from '@/components/IncidentList.vue'
import FilterHeader from '@/components/FilterHeader.vue'

export default {
  components: {
    IncidentDetails,
    IncidentList,
    FilterHeader,
  },
  props: {
    city: {
      type: String,
      default: '',
    },
  },
}
</script>
