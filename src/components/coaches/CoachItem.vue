<template>
<li>
<h3>{{ fullName }}</h3>
<h4>${{ rate }}/hour</h4>
<div>
      <base-badge v-for="area in areas" :key="area" :type="area" :title="area">{{ area }}</base-badge>
</div>
<div class="action">
      <base-button mode="outline" :to="coachContactLink">Contact</base-button>  <!--or  to="/coaches/c1/contact" -->
      <base-button link :to="coachDetailsLink">View Details</base-button> <!-- or to="/coaches/c1"-->
</div>
</li>
</template>

<script>
import BaseButton from '../ui/BaseButton.vue';
import BaseBadge from '../ui/BaseBadge.vue';

export default {
    props: ["id", "firstName", "lastName", "rate", "areas"],
    computed: {
        fullName() {
            return this.firstName + " " + this.lastName;
        },
        coachContactLink() {
            // this.$route.path + '/' same as => /coaches/
            return this.$route.path + "/" + this.id + "/contact/"; // /coaches/c1/contact
        },
        coachDetailsLink() {
            return this.$route.path + "/" + this.id; // /coaches/c1
        }
    },
    components: { BaseButton, BaseBadge }
}
</script>

<style scoped>
li {
  margin: 1rem 0;
  border: 1px solid #424242;
  border-radius: 12px;
  padding: 1rem;
}

h3 {
  font-size: 1.5rem;
}

h3,
h4 {
  margin: 0.5rem 0;
}

div {
  margin: 0.5rem 0;
}

.actions {
  display: flex;
  justify-content: flex-end;
}
</style>