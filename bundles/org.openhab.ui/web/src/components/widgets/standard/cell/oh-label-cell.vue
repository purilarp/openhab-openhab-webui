<template>
  <oh-cell :context="context" class="label-cell">
    <template v-slot:header>
      <f7-list media-list>
        <f7-list-item media-item :subtitle="config.subtitle" :footer="config.footer">
          <div slot="title" class="button-header display-flex">
            <oh-icon class="header-icon" v-if="config.icon && config.icon.indexOf('oh:') === 0" :icon="config.icon.substring(3)" width="20" height="20"></oh-icon>
            <f7-icon class="header-icon" v-if="config.icon && config.icon.indexOf('oh:') < 0" :f7="config.icon.substring(3)" size="20"></f7-icon>
            <span>{{config.title || config.header}}</span>
            <f7-badge v-if="config.headerBadge" color="config.headerBadgeColor">{{config.headerBadge}}</f7-badge>
          </div>
          <div class="state" :style="config.stateStyle">{{config.label || context.store[config.item].displayState || context.store[config.item].state}}</div>
        </f7-list-item>
      </f7-list>
    </template>
  </oh-cell>
</template>

<style lang="stylus">
.label-cell
  --oh-label-cell-state-font-size 24px
  .state
    font-weight normal
    font-size var(--oh-label-cell-state-font-size)
</style>

<script>
import mixin from '../../widget-mixin'
import { OhLabelCellDefinition } from '@/assets/definitions/widgets/standard/cells'
import OhCell from './oh-cell.vue'

export default {
  mixins: [mixin],
  components: {
    OhCell
  },
  widget: OhLabelCellDefinition
}
</script>
