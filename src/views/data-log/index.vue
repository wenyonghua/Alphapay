<script setup lang="ts">
import { ref, reactive } from "vue";
import { ElMessage } from 'element-plus'
import { findTradeSituation } from '~/api/api';
import { useRouter, useRoute } from 'vue-router'
import { useStore } from '~/store/store';
import { fa } from "element-plus/es/locale";

const store = useStore()

const router = useRouter();
const route = useRoute();

const loading = ref(true);

interface  DataLog {
  totalTradeAmount: number
  totalPoundage: number
  totalActualIncome: number
  totalPaidOrderNum: number
  totalOrderNum: number
  totalSuccessRate: number

  monthTradeAmount: number
  monthPoundage: number
  monthActualIncome: number
  monthOrderNum: number
  monthPaidOrderNum: number
  monthSuccessRate: number

  todayTradeAmount: number
  todayPoundage: number
  todayActualIncome: number
  todayOrderNum: number
  todayPaidOrderNum: number
  todaySuccessRate: number

  yesterdayTradeAmount: number
  yesterdayPoundage: number
  yesterdayActualIncome: number
  yesterdayOrderNum: number
  yesterdayPaidOrderNum: number
  yesterdaySuccessRate: number
}

let sitlog = reactive({data: <DataLog>{}});
findTradeSituation().then(res => {
    sitlog.data = res.data.data;
    loading.value = false;
})

</script>

<template>
  <div class="charts-box">
    <div class="card-box">
    <el-card v-loading="loading" class="box-card">
        <template #header>
        <div class="card-header">
            <span>{{$t('datalog.title1')}}</span>
            <!-- <el-button class="button" type="primary">重置</el-button> -->
        </div>
        </template>
        <div>
            <h1>{{sitlog.data.totalTradeAmount}}VAD</h1>
        </div>
        <div class="tips">
            <p>{{$t('datalog.service_charge')}}: <span>{{sitlog.data.totalPoundage}}VAD</span></p>
            <p>{{$t('datalog.paid_in_amount')}}: <span>{{sitlog.data.totalActualIncome}}VAD</span></p>
        </div>
        <div class="tips">
            <p>{{$t('datalog.order_quantity_paid')}}: <span>{{sitlog.data.totalPaidOrderNum}}</span></p>
            <p>{{$t('datalog.order_quantity')}}: <span>{{sitlog.data.totalOrderNum}}</span></p>
            <p>{{$t('datalog.success_rate')}}: <span>{{sitlog.data.totalSuccessRate}}%</span></p>
        </div>
  </el-card>
  <el-card v-loading="loading" class="box-card">
        <template #header>
        <div class="card-header">
            <span>{{$t('datalog.title3')}}</span>
            <!-- <el-button class="button" type="primary">重置</el-button> -->
        </div>
        </template>
        <div>
            <h1>{{sitlog.data.monthTradeAmount}}VAD</h1>
        </div>
        <div class="tips">
            <p>{{$t('datalog.service_charge')}}: <span>{{sitlog.data.monthPoundage}}VAD</span></p>
            <p>{{$t('datalog.paid_in_amount')}}: <span>{{sitlog.data.monthActualIncome}}VAD</span></p>
        </div>
        <div class="tips">
            <p>{{$t('datalog.order_quantity_paid')}}: <span>{{sitlog.data.monthPaidOrderNum}}</span></p>
            <p>{{$t('datalog.order_quantity')}}: <span>{{sitlog.data.monthOrderNum}}</span></p>
            <p>{{$t('datalog.success_rate')}}: <span>{{sitlog.data.monthSuccessRate}}%</span></p>
        </div>
  </el-card>
  </div>
  <div class="card-box">
  <el-card v-loading="loading" class="box-card">
        <template #header>
        <div class="card-header">
            <span>{{$t('datalog.title2')}}</span>
            <!-- <el-button class="button" type="primary">重置</el-button> -->
        </div>
        </template>
        <div>
            <h1>{{sitlog.data.yesterdayTradeAmount}}VAD</h1>
        </div>
        <div class="tips">
            <p>{{$t('datalog.service_charge')}}: <span>{{sitlog.data.yesterdayPoundage}}VAD</span></p>
            <p>{{$t('datalog.paid_in_amount')}}: <span>{{sitlog.data.yesterdayActualIncome}}VAD</span></p>
        </div>
        <div class="tips">
            <p>{{$t('datalog.order_quantity_paid')}}: <span>{{sitlog.data.yesterdayPaidOrderNum}}</span></p>
            <p>{{$t('datalog.order_quantity')}}: <span>{{sitlog.data.yesterdayOrderNum}}</span></p>
            <p>{{$t('datalog.success_rate')}}: <span>{{sitlog.data.yesterdaySuccessRate}}%</span></p>
        </div>
  </el-card>
  <el-card v-loading="loading" class="box-card">
        <template #header>
        <div class="card-header">
            <span>{{$t('datalog.title4')}}</span>
            <!-- <el-button class="button" type="primary">重置</el-button> -->
        </div>
        </template>
        <div>
            <h1>{{sitlog.data.todayTradeAmount}}VAD</h1>
        </div>
        <div class="tips">
            <p>{{$t('datalog.service_charge')}}: <span>{{sitlog.data.todayPoundage}}VAD</span></p>
            <p>{{$t('datalog.paid_in_amount')}}: <span>{{sitlog.data.todayActualIncome}}VAD</span></p>
        </div>
        <div class="tips">
            <p>{{$t('datalog.order_quantity_paid')}}: <span>{{sitlog.data.todayPaidOrderNum}}</span></p>
            <p>{{$t('datalog.order_quantity')}}: <span>{{sitlog.data.todayOrderNum}}</span></p>
            <p>{{$t('datalog.success_rate')}}: <span>{{sitlog.data.todaySuccessRate}}%</span></p>
        </div>
  </el-card>
    </div>
  </div>
</template>

<style lang="scss" scoped>
$bg:#2d3a4b;
$dark_gray:#889aa4;
$light_gray:#eee;
.charts-box {
    height: calc(100% - 80px);
    overflow-y: scroll;
}
.card-box {
    padding: 20px 20px 0 20px;
    display: flex;
    justify-content: space-between;
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
    width: 570px;
    // margin-right: 20px;
}
</style>
