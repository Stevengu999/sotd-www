<template>
<ul class="component-DappBadgeList">
  <li class="item" v-for="(badge, index) in badges" :key="index">
    <span class="popover">{{ badge | formatDappBadge }}</span>
    <component :is="svgBadgeComponent(badge)" :width="12" :height="14"></component>
  </li>
</ul>
</template>

<script>
import { dappBadgeComponentMap } from '~/helpers/constants'
import SvgBadge0x from './SvgBadge0x'
import SvgBadgeComplete from './SvgBadgeComplete'
import SvgBadgeConsensys from './SvgBadgeConsensys'
import SvgBadgeFeatured from './SvgBadgeFeatured'
import SvgBadgeHot from './SvgBadgeHot'
import SvgBadgeMetamask from './SvgBadgeMetamask'
import SvgBadgeSolidified from './SvgBadgeSolidified'
import SvgBadgeStatus from './SvgBadgeStatus'
import SvgBadgeToken from './SvgBadgeToken'

export default {
  components: {
    SvgBadge0x,
    SvgBadgeComplete,
    SvgBadgeConsensys,
    SvgBadgeFeatured,
    SvgBadgeHot,
    SvgBadgeMetamask,
    SvgBadgeSolidified,
    SvgBadgeStatus,
    SvgBadgeToken
  },
  methods: {
    svgBadgeComponent (badge) {
      const badgeComponent = dappBadgeComponentMap[badge]
      return badgeComponent
    }
  },
  props: {
    badges: {
      type: Array
    }
  }
}
</script>

<style lang="scss" scoped>
@import '~assets/css/settings';

.component-DappBadgeList {
  display: flex;
  align-items: center;
}

.item {
  display: flex;
  align-items: center;
  margin-left: 3px;
  position: relative;
}

.popover {
  opacity: 0;
  position: absolute;
  right: -5px;
  bottom: 20px;
  white-space: nowrap;
  text-transform: uppercase;
  font-size: .8rem;
  font-weight: 600;
  height: 25px;
  line-height: 26px;
  padding: 0 10px;
  border-radius: 4px;
  background: rgba($color--white, .85);
  transition: opacity .3s ease;
  box-shadow: 0 5px 10px rgba($color--black, .15);
  &:after {
    content: '';
    position: absolute;
    right: 6px;
    bottom: -5px;
    width: 0;
    height: 0;
    border-left: 5px solid transparent;
    border-right: 5px solid transparent;
    border-top: 5px solid rgba($color--white, .9);
  }
  .item:hover & {
    opacity: 1;
  }
}
</style>
