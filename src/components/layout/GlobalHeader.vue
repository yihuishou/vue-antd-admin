<template>
  <a-layout-header class="global-header">
    <router-link v-if="isMobile" to="/" class="logo">
      <img width="32" src="static/img/vue-antd-logo.png" />
    </router-link>
    <a-divider v-if="isMobile" type="vertical" />
    <a-icon class="trigger" :type="collapsed ? 'menu-unfold' : 'menu-fold'" @click="toggleCollapse"/>
    <div style="float: right">
        <header-search class="header-item" />
        <a-tooltip class="header-item" title="帮助文档" placement="bottom" >
          <a>
            <a-icon type="question-circle-o" />
          </a>
        </a-tooltip>
        <header-notice class="header-item"/>
        <header-avatar class="header-item"/>
    </div>
  </a-layout-header>
</template>

<script>
import ALayout from 'ant-design-vue/es/layout'
import AIcon from 'ant-design-vue/es/icon/icon'
import AInputSearch from 'ant-design-vue/es/input/Search'
import HeaderSearch from './HeaderSearch'
import HeaderNotice from './HeaderNotice'
import ATooltip from 'ant-design-vue/es/tooltip/Tooltip'
import HeaderAvatar from './HeaderlAvatar'
import ADivider from 'ant-design-vue/es/divider/index'

const ALayoutSider = ALayout.Sider
const ALayoutHeader = ALayout.Header
export default {
  name: 'GlobalHeader',
  components: {
    ADivider,
    HeaderAvatar,
    ATooltip,
    HeaderNotice,
    HeaderSearch,
    AInputSearch,
    AIcon,
    ALayout,
    ALayoutSider,
    ALayoutHeader},
  props: ['collapsed'],
  computed: {
    isMobile () {
      return this.$store.state.setting.isMobile
    }
  },
  methods: {
    toggleCollapse () {
      this.$emit('toggleCollapse')
    }
  }
}
</script>

<style lang="less" scoped>
  .trigger {
    font-size: 20px;
    line-height: 64px;
    padding: 0 24px;
    cursor: pointer;
    transition: color .3s;
  }

  .trigger:hover {
    color: #1890ff;
  }

  .header-item{
    padding: 0 12px;
    display: inline-block;
    height: 100%;
    cursor: pointer;
    vertical-align: middle;
    i{
      font-size: 16px;
      color: rgba(0,0,0,.65);
    }
  }
  .global-header{
    background: #fff;
    padding: 0 12px 0 0;
    -webkit-box-shadow: 0 1px 4px rgba(0,21,41,.08);
    box-shadow: 0 1px 4px rgba(0,21,41,.08);
    position: relative;
    .logo {
      height: 64px;
      line-height: 58px;
      vertical-align: top;
      display: inline-block;
      padding: 0 12px 0 24px;
      cursor: pointer;
      font-size: 20px;
      img {
        display: inline-block;
        vertical-align: middle;
      }
    }
  }
</style>
