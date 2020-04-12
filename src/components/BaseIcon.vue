<template>
  <div class="icon-wrapper">
    <svg class="icon" :width="width" :height="height">
      <use v-bind="{ 'xlink:href': '/feather-sprite.svg#' + name }"></use>
    </svg>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator';
@Component
class BaseIcon extends Vue {
  @Prop({
    type: String,
    required: true,
  })
  private name!: string;
  @Prop({
    type: [Number, String],
    required: true,
    default: 24,
  })
  private width!: number | string;
  @Prop({
    type: [Number, String],
    required: true,
    default: 24,
  })
  private height!: number | string;
}

export default BaseIcon;
</script>

<style lang="scss" scoped>
.icon-wrapper {
  display: inline-flex;
  align-items: center;
  color: rgba(0, 0, 0, 0.4);
  font-size: 1rem;
  font-weight: 600;
}
.icon {
  stroke: currentColor;
  stroke-width: 2;
  stroke-linecap: round;
  stroke-linejoin: round;
  fill: none;
  margin-right: 6px;
}
</style>
