<template>
<section>FILTER</section>
<section>
      <base-card>
            <div class="controls">
                  <base-button mode="outline">Refresh</base-button>
                  <base-button link to="/register">Register as Coach</base-button>
            </div>
            <ul v-if="hasCoaches">
                  <CoachItem v-for="coach in filteredCoaches" 
                  :key="coach.id" 
                  :id="coach.id" 
                  :first-name="coach.firstName" 
                  :last-name="coach.lastName" 
                  :rate="coach.hourlyRate" 
                  :areas="coach.areas"></CoachItem>
            </ul>
            <h3 v-else>No coaches found.</h3>
      </base-card>
</section>
</template>

<script>
import CoachItem from '../../components/coaches/CoachItem.vue';
import BaseCard from '../../components/ui/BaseCard.vue';
import BaseButton from '../../components/ui/BaseButton.vue';
export default {
      computed: {
            filteredCoaches() {
                  return this.$store.getters['coaches/coaches']; //1st coaches- namespace name, 2nd /coaches - the getter name
            },
            hasCoaches() {
                  return this.$store.getters['coaches/hasCoaches'];
            }
      },
      components: {
    CoachItem,
    BaseCard,
    BaseButton,
}
}
</script>
