<template>
  <div class="home">
      <RouteCards></RouteCards>
  </div>
</template>

<script>
// @ is an alias to /src
import RouteCards from '@/components/RouteCards.vue'

export default {
  name: 'HomeView',
  components: {
    RouteCards
  }
}
</script>
