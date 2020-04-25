<template>
  <h1>Create Event, {{ userName }}</h1>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
@Component
class EventCreate extends Vue {
  get userName() {
    return this.$store.state.user.name;
  }
}

export default EventCreate;
</script>
