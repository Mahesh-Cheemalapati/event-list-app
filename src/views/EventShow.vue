<template>
  <h1>Showing event #{{ id }}</h1>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator';

@Component
class EventShow extends Vue {
  @Prop({
    required: true,
    type: Number,
  })
  private id!: number;
}

export default EventShow;
</script>
