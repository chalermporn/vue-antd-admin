<template>
  <div class="page-header">
    <div class="breadcrumb">
      <a-breadcrumb>
        <a-breadcrumb-item><a href="#/dashboard">首页</a></a-breadcrumb-item>
        <a-breadcrumb-item :key="item.path" v-for="item in breadcrumb">{{item.name}}</a-breadcrumb-item>
      </a-breadcrumb>
    </div>
    <div class="detail">
      <div v-if="avatar" class="avatar"><a-avatar :src="avatar" /></div>
      <div class="main">
        <div class="row">
          <img v-if="logo" :src="logo" class="logo" />
          <h1 v-if="title" class="title">{{title}}</h1>
          <div class="action"><slot name="action"></slot></div>
        </div>
        <div class="row">
          <div v-if="this.$slots.content" class="content"><slot name="content"></slot></div>
          <div v-if="this.$slots.extra" class="extra"><slot name="extra"></slot></div>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
import ABreadcrumb from 'vue-antd-ui/es/breadcrumb'
import AAvatar from 'vue-antd-ui/es/avatar/Avatar'

const ABreadcrumbItem = ABreadcrumb.Item
export default {
  name: 'PageHeader',
  components: {AAvatar, ABreadcrumbItem, ABreadcrumb},
  props: {
    title: {
      type: String,
      required: false
    },
    breadcrumb: {
      type: Array,
      required: false
    },
    logo: {
      type: String,
      required: false
    },
    avatar: {
      type: String,
      required: false
    }
  }
}
</script>

<style lang="less" scoped>
  .page-header{
    background: #fff;
    padding: 16px 32px 0;
    border-bottom: 1px solid #e8e8e8;
    .breadcrumb{
      margin-bottom: 16px;
    }
    .detail{
      display: flex;
      .row {
        display: flex;
        width: 100%;
      }
      .avatar {
        flex: 0 1 72px;
        margin-bottom: 8px;
        & > span {
          border-radius: 72px;
          display: block;
          width: 72px;
          height: 72px;
        }
      }
      .main{
        width: 100%;
        flex: 0 1 auto;
        .title{
          flex: auto;
          font-size: 20px;
          font-weight: 500;
          color: rgba(0,0,0,.85);
          margin-bottom: 16px;
        }
        .logo{
          width: 28px;
          height: 28px;
          border-radius: 4px;
          margin-right: 16px;
        }
        .content{
          margin-bottom: 16px;
          flex: auto;
        }
        .extra{
          flex: 0 1 auto;
          margin-left: 88px;
          min-width: 242px;
          text-align: right;
        }
        .action{
          margin-left: 56px;
          min-width: 266px;
          flex: 0 1 auto;
          text-align: right;
        }
      }
    }
  }
</style>
