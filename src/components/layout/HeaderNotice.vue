<template>
  <a-popover trigger="click" placement="bottomRight" :overlayStyle="{ width: '300px' }">
    <template slot="content">
      <a-spin :spinning="loadding">
        <a-tabs>
          <a-tab-pane tab="通知" key="1">
            <a-list>
              <a-list-item>
                <a-list-item-meta title="你收到了 14 份新周报" description="一年前">
                  <a-avatar style="background-color: white" slot="avatar" src="https://gw.alipayobjects.com/zos/rmsportal/ThXAXghbEsBCCSDihZxY.png"/>
                </a-list-item-meta>
              </a-list-item>
              <a-list-item>
                <a-list-item-meta title="你推荐的 曲妮妮 已通过第三轮面试" description="一年前">
                  <a-avatar style="background-color: white" slot="avatar" src="https://gw.alipayobjects.com/zos/rmsportal/OKJXDXrmkNshAMvwtvhu.png"/>
                </a-list-item-meta>
              </a-list-item>
              <a-list-item>
                <a-list-item-meta title="这种模板可以区分多种通知类型" description="一年前">
                  <a-avatar style="background-color: white" slot="avatar" src="https://gw.alipayobjects.com/zos/rmsportal/kISTdvpyTAhtGxpovNWd.png"/>
                </a-list-item-meta>
              </a-list-item>
            </a-list>
          </a-tab-pane>
          <a-tab-pane tab="消息" key="2">
            123
          </a-tab-pane>
          <a-tab-pane tab="待办" key="3">
            123
          </a-tab-pane>
        </a-tabs>
      </a-spin>
    </template>
    <span @click="fetchNotice" class="header-notice">
      <a-badge count="12">
        <a-icon style="font-size: 16px; padding: 4px" type="bell" />
      </a-badge>
    </span>
  </a-popover>
</template>

<script>
import APopover from 'ant-design-vue/es/popover/index'
import AIcon from 'ant-design-vue/es/icon/icon'
import ABadge from 'ant-design-vue/es/badge/Badge'
import ATabs from 'ant-design-vue/es/tabs'
import AList from 'ant-design-vue/es/list/index'
import AListItem from 'ant-design-vue/es/list/Item'
import AAvatar from 'ant-design-vue/es/avatar/Avatar'
import ASpin from 'ant-design-vue/es/spin/Spin'

const ATabPane = ATabs.TabPane
const AListItemMeta = AListItem.Meta

export default {
  name: 'HeaderNotice',
  components: {ASpin, AAvatar, AListItem, AList, ATabs, ABadge, AIcon, APopover, ATabPane, AListItemMeta},
  data () {
    return {
      loadding: false
    }
  },
  methods: {
    fetchNotice () {
      if (this.loadding) {
        this.loadding = false
        return
      }
      this.loadding = true
      setTimeout(() => {
        this.loadding = false
      }, 2000)
    }
  }
}
</script>

<style lang="less">
  .header-notice{
    display: inline-block;
    transition: all 0.3s;
    & :global{
      span {
        vertical-align: initial;
      }
    }
  }
</style>
