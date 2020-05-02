<template>
  <div>
    <!-- 面包屑导航区域 -->
    <el-breadcrumb separator-class="el-icon-arrow-right">
      <el-breadcrumb-item :to="{ path: '/home' }">首页</el-breadcrumb-item>
      <el-breadcrumb-item>订单管理</el-breadcrumb-item>
      <el-breadcrumb-item>订单列表</el-breadcrumb-item>
    </el-breadcrumb>

    <!-- 卡片视图区域 -->
    <el-card>
      <el-row>
        <el-col :span="8">
          <el-input placeholder="请输入内容">
            <el-button slot="append" icon="el-icon-search"></el-button>
          </el-input>
        </el-col>
      </el-row>

      <!-- 订单列表数据 -->
      <el-table :data="orderlist" border stripe>
        <el-table-column type="index"></el-table-column>
        <el-table-column label="订单编号" prop="order_number"></el-table-column>
        <el-table-column label="订单价格" prop="order_price"></el-table-column>
        <el-table-column label="是否付款" prop="pay_status">
          <template>
            <el-tag type="success">已付款</el-tag>
            <el-tag type="danger">未付款</el-tag>
          </template>
        </el-table-column>
        <el-table-column label="是否发货" prop="is_send">
        </el-table-column>
        <el-table-column label="下单时间" prop="create_time">
        </el-table-column>
        <el-table-column label="操作">
          <template>
            <el-button size="mini" type="primary" icon="el-icon-edit" @click="showBox"></el-button>
            <el-button size="mini" type="success" icon="el-icon-location" @click="showProgressBox"></el-button>
          </template>
        </el-table-column>
      </el-table>
      <!-- 分页区域 -->
      <el-pagination class="cat_opt"> </el-pagination>
    </el-card>
  </div>
</template>

<script>
export default {
  data () {
    return {
      orderlist: []
    }
  },
  created () {
    this.getOrderList()
  },
  methods: {
    getOrderList () {
      this.orderlist = [
        {
          order_number: '12',
          order_price: '88',
          pay_status: 1
        },
        {
          order_number: '12',
          order_price: '88',
          pay_status: 1
        },
        {
          order_number: '12',
          order_price: '88',
          pay_status: 1
        },
        {
          order_number: '12',
          order_price: '88',
          pay_status: 1
        },
        {
          order_number: '12',
          order_price: '88',
          pay_status: 1
        }
      ]
    }
  }
}
</script>
<style lang="less" scoped></style>
