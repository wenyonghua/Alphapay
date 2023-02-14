<template>
  <div class="left-wrap">
    <div class="user-info">
      <div>
        <img width="60" src="../../assets/default-avatar.webp" />
      </div>
      <div class="user-desc">
        <div class="name">{{props.userName || 'admin'}}</div>
        <div class="tool">
          <div class="status"><el-icon><User color="#21ba45"/></el-icon><span>{{$t('side_bar.online')}}</span></div>
          <div class="logout" @click="props.logout()"><el-icon><SwitchButton color="#db2828" /></el-icon><span>{{$t('side_bar.logout')}}</span></div>
        </div>
      </div>
    </div>
    <el-menu
    default-active="2"
    class="el-menu-vertical-demo"
    router
    :collapse="isCollapse"
    @open="handleOpen"
    @close="handleClose"
  >
    <el-menu-item index="/">
      <el-icon><House /></el-icon>
      <template #title>{{$t('side_bar.homepage')}}</template>
      </el-menu-item>
    <el-sub-menu index="1">
      <template #title>
        <el-icon><notebook /></el-icon>
        <span>{{$t('side_bar.create_settlement')}}</span>
      </template>
      <el-menu-item-group>
        <template #title><span>{{$t('side_bar.settlement')}}</span></template>
        <el-menu-item index="/apply-settlement">{{$t('side_bar.create_settlement')}}</el-menu-item>
        <el-menu-item index="/history-settlement">{{$t('side_bar.settlement_history')}}</el-menu-item>
      </el-menu-item-group>
    </el-sub-menu>
    <el-menu-item index="/statistical-analysis">
      <el-icon><tickets /></el-icon>
      <template #title>{{$t('side_bar.merchant_order')}}</template>
    </el-menu-item>
    <el-menu-item index="/bank-management">
      <el-icon><postcard /></el-icon>
      <template #title>{{$t('side_bar.bank_management')}}</template>
    </el-menu-item>
    <el-menu-item index="/merchant-paylist">
      <el-icon><wallet /></el-icon>
      <template #title>{{$t('side_bar.transaction_history')}}</template>
    </el-menu-item>
    <el-menu-item index="/payoutmerchant-order">
      <el-icon><creditCard /></el-icon>
      <template #title>{{$t('side_bar.payoutmerchant_order')}}</template>
    </el-menu-item>
    <el-menu-item index="/merchant-info">
      <el-icon><setting /></el-icon>
      <template #title>{{$t('side_bar.merchant_info')}}</template>
    </el-menu-item>
  </el-menu>
  </div>
</template>

<style lang="scss" scoped>
.left-wrap {
  min-width: 240px;
}
.el-menu {
  min-height: 600px;
}
.user-info {
  font-size: 14px;
  display: flex;
  padding: 20px 20px;
  border-right: 1px solid #dcdfe6;
  img {
    width: 50px;
    height: 50px;
    border-radius: 100%;
  }
  .user-desc {
    margin-left: 10px;
    padding: 4px 0;
    .name {
      font-weight: bold;
    }
  }
  .tool {
    margin-top: 6px;
    font-size: 12px;
    display: flex;
    justify-content: space-between;
    .logout {
      cursor: pointer;
      margin-left: 10px;
    }
    span {
      vertical-align: 1px;
      margin-left: 2px;
    }
  }
}
</style>

<script lang="ts" setup>
import { ref } from 'vue'
import {
  Notebook,
  Postcard,
  Tickets,
  Wallet,
  Setting,
  User,
  SwitchButton,
  House,
  CreditCard
} from '@element-plus/icons-vue'

const props = defineProps<{ switchLang: any, logout: any, userName: string }>();
const isCollapse = ref(false)
const handleOpen = (key: string, keyPath: string[]) => {
  console.log(key, keyPath)
}
const handleClose = (key: string, keyPath: string[]) => {
  console.log(key, keyPath)
}
</script>

