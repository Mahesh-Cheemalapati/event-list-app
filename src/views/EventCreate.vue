<template>
  <div>
    <h1>Create an Event</h1>
    <form>
      <label>Select a category</label>
      <select v-model="createFreshEvent.model">
        <option v-for="cat in categories" :key="cat"> {{ cat }}</option>
      </select>

      <h3>Event Title</h3>
      <div class="field">
        <label>Title</label>
        <input
          v-model="createFreshEvent.title"
          type="text"
          placeholder="Add an event title"
        />
      </div>
      <div class="field">
        <label>Description</label>
        <input
          v-model="createFreshEvent.description"
          type="text"
          placeholder="Add a description"
        />
      </div>

      <h3>Event Location</h3>
      <div class="field">
        <label>Location</label>
        <input
          v-model="createFreshEvent.location"
          type="text"
          placeholder="Add a location"
        />
      </div>

      <h3>When is your event?</h3>
      <div class="field">
        <label>Date</label>
        <datepicker
          v-model="createFreshEvent.date"
          placeholder="Select a date"
        />
      </div>
      <div class="field">
        <label>Select a time</label>
        <select v-model="createFreshEvent.time">
          <option v-for="time in times" :key="time">{{ time }}</option>
        </select>
      </div>
      <input type="submit" class="button -fill-gradient" value="Submit" />
    </form>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Datepicker from 'vue';

@Component({
  components: {
    Datepicker,
  },
})
class EventCreate extends Vue {
  data() {
    const times = [];
    for (let i = 1; i <= 24; i++) {
      times.push(i + ':00');
    }
    return {
      event: this.createFreshEvent,
      times,
      categories: this.$store.state.categories,
    };
  }

  get createFreshEvent() {
    const user = this.$store.state.user;
    const id = Math.floor(Math.random() * 10000000);
    return {
      id: id,
      organizer: user,
      category: '',
      title: '',
      location: '',
      date: '',
      time: '',
      attendees: [],
    };
  }
}

export default EventCreate;
</script>
