<script setup lang="ts">
import { ref, reactive } from "vue";
import { ElMessage } from 'element-plus'
import { findTradeSituation } from '~/api/api';
import { useRouter, useRoute } from 'vue-router'
import { useStore } from '~/store/store';

const store = useStore()

const router = useRouter();
const route = useRoute();

let data = ref(null);
findTradeSituation().then(res => {
    data = res.data.data;
})

</script>

<template>
  <div class="charts-box">
    <div class="card-box">
    <el-card class="box-card">
        <template #header>
        <div class="card-header">
            <span>{{$t('datalog.title1')}}</span>
            <!-- <el-button class="button" type="primary">重置</el-button> -->
        </div>
        </template>
        <div>
            <h1>15,334</h1>
        </div>
        <div class="tips">
            <p>{{$t('datalog.service_charge')}}: <span>1231</span></p>
            <p>{{$t('datalog.paid_in_amount')}}: <span>1231</span></p>
        </div>
        <div class="tips">
            <p>{{$t('datalog.order_quantity_paid')}}: <span>1231</span></p>
            <p>{{$t('datalog.order_quantity')}}: <span>1231</span></p>
            <p>{{$t('datalog.success_rate')}}: <span>12%</span></p>
        </div>
  </el-card>
  <el-card class="box-card">
        <template #header>
        <div class="card-header">
            <span>{{$t('datalog.title2')}}</span>
            <!-- <el-button class="button" type="primary">重置</el-button> -->
        </div>
        </template>
        <div>
            <h1>15,334</h1>
        </div>
        <div class="tips">
            <p>{{$t('datalog.service_charge')}}: <span>1231</span></p>
            <p>{{$t('datalog.paid_in_amount')}}: <span>1231</span></p>
        </div>
        <div class="tips">
            <p>{{$t('datalog.order_quantity_paid')}}: <span>1231</span></p>
            <p>{{$t('datalog.order_quantity')}}: <span>1231</span></p>
            <p>{{$t('datalog.success_rate')}}: <span>12%</span></p>
        </div>
  </el-card>
  <el-card class="box-card">
        <template #header>
        <div class="card-header">
            <span>{{$t('datalog.title3')}}</span>
            <!-- <el-button class="button" type="primary">重置</el-button> -->
        </div>
        </template>
        <div>
            <h1>15,334</h1>
        </div>
        <div class="tips">
            <p>{{$t('datalog.service_charge')}}: <span>1231</span></p>
            <p>{{$t('datalog.paid_in_amount')}}: <span>1231</span></p>
        </div>
        <div class="tips">
            <p>{{$t('datalog.order_quantity_paid')}}: <span>1231</span></p>
            <p>{{$t('datalog.order_quantity')}}: <span>1231</span></p>
            <p>{{$t('datalog.success_rate')}}: <span>12%</span></p>
        </div>
  </el-card>
  <el-card class="box-card">
        <template #header>
        <div class="card-header">
            <span>{{$t('datalog.title4')}}</span>
            <!-- <el-button class="button" type="primary">重置</el-button> -->
        </div>
        </template>
        <div>
            <h1>15,334</h1>
        </div>
        <div class="tips">
            <p>{{$t('datalog.service_charge')}}: <span>1231</span></p>
            <p>{{$t('datalog.paid_in_amount')}}: <span>1231</span></p>
        </div>
        <div class="tips">
            <p>{{$t('datalog.order_quantity_paid')}}: <span>1231</span></p>
            <p>{{$t('datalog.order_quantity')}}: <span>1231</span></p>
            <p>{{$t('datalog.success_rate')}}: <span>12%</span></p>
        </div>
  </el-card>
    </div>
  </div>
</template>

<style lang="scss" scoped>
$bg:#2d3a4b;
$dark_gray:#889aa4;
$light_gray:#eee;
.card-box {
    padding: 20px;
    display: flex;
    h1 {
        color: #da3764;
    }
    .card-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .tips {
        &:last-child {
            display: block;
        }
        display: flex;
        justify-content: space-between;
        p {
            margin-right: 20px;
            span {
                font-weight: bold;
            }
        }
    }
}
.el-card {
    width: 270px;
    margin-right: 20px;
}
</style>
