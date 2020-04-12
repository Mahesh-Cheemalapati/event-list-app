<template>
  <div>
    <h1>Events Listing</h1>
    <event-card v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import EventCard from '@/components/EventCard.vue';
import axios from 'axios';

@Component({
  components: {
    EventCard,
  },
})
class EventList extends Vue {
  data() {
    return {
      events: [],
    };
  }
  created() {
    axios
      .get('http://localhost:3000/events')
      .then(Response => {
        this.events = Response.data;
      })
      .catch(Error => {
        console.log(Error);
      });
  }

  private events = [];
}

export default EventList;
</script>
