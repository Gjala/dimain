<template>
  <div class="events">
    <img alt="Vue logo" src="../assets/logo.png" />
    <h4>Events for Good</h4>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from "@/components/EventCard.vue";
import EventService from '@/services/EventService.js'

export default {
  name: "EventsList",
  components: {
    EventCard
  },
  data(){
    return{
      events: null
    }
  },
  created(){
    EventService.getEvents()
    .then(response => {
      this.events = response.data
    })
    .catch(error => {
      console.log(error);
    })
  }
};
</script>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
