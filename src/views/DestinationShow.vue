<template>
  <section>
      <h1>{{ destination.name }}</h1>
      <div class="destination-details">
          <img :src="`/images/${destination.image}`" :alt="destination.name">
          <p>{{ destination.description }}</p>
      </div>
  </section>
</template>

<script>

import { computed, defineComponent} from 'vue'
import { useRoute } from 'vue-router'
import sourceData from '@/data.json'

export default defineComponent ({
    setup() {
        const route = useRoute();
        // Now you can access params like:
        console.log(route.params.id);

        const destinationId = computed(() => {
            return parseInt(route.params.id)
        })

        const destination = computed(() => {
            return sourceData.destinations.find(destination => destination.id === destinationId.value)
        })


        return { destination }
    }
})
</script>

<style>

</style>