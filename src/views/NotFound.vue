<template>
  <div id="app">
    <the-header />
    <div :class="$style.wrapper">
      <center-wrapper>
        <h2>404: File not found</h2>
        <p>
          Uh-oh, this URL does not exist.
          <router-link to="/">Click here to return home</router-link>
        </p>
      </center-wrapper>
    </div>
  </div>
</template>

<script>
import TheHeader from '@/components/TheHeader.vue'
import CenterWrapper from '@/components/CenterWrapper.vue'

export default {
  components: {
    TheHeader,
    CenterWrapper,
  },
}
</script>

<style module lang="postcss">
.wrapper {
  background: var(--color-white);
  padding: 1.5em 0;
  bottom: 0;
}
</style>
