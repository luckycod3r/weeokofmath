<template>
  <div class="route-cards">
    <RouteCard icon="puzzle-piece" name="Тест на знание" :path="'test'"/>
    <RouteCard icon="graduation-cap" name="Образовательный контент"/>
  </div>
</template>

<script>
import RouteCard from './RouteCard.vue';


export default {
  name: 'route-cards',
  components: {
    RouteCard
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.route-cards{
  max-width: 90vw;
  margin: 0 auto;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-items: center;
}
</style>
