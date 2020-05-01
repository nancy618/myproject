<template>
  <div>
    <!-- 面包屑导航区域 -->
    <el-breadcrumb separator-class="el-icon-arrow-right">
      <el-breadcrumb-item :to="{ path: '/home' }">首页</el-breadcrumb-item>
      <el-breadcrumb-item>商品管理</el-breadcrumb-item>
      <el-breadcrumb-item>商品列表</el-breadcrumb-item>
    </el-breadcrumb>

    <!-- 卡片视图区域 -->
    <el-card>
      <el-row :gutter="20">
        <el-col :span="8">
          <el-input placeholder="请输入内容">
            <el-button
              slot="append"
              icon="el-icon-search"
              @click="getGoodsList"
            ></el-button>
          </el-input>
        </el-col>
        <el-col :span="4">
          <el-button type="primary" @click="goAddpage">添加商品</el-button>
        </el-col>
      </el-row>

      <!-- table表格区域 -->
      <el-table :data="goodslist" border stripe>
        <el-table-column type="index"></el-table-column>
        <el-table-column label="商品名称" prop="goods_name"></el-table-column>
        <el-table-column
          label="商品价格(元)"
          prop="goods_price"
          width="95px"
        ></el-table-column>
        <el-table-column
          label="商品重量"
          prop="goods_weight"
          width="70px"
        ></el-table-column>
        <el-table-column label="创建时间" prop="add_time" width="140px">
        </el-table-column>
        <el-table-column label="操作" width="130px">
          <template>
            <el-button
              type="primary"
              icon="el-icon-edit"
              size="mini"
            ></el-button>
            <el-button
              type="danger"
              icon="el-icon-delete"
              size="mini"
            ></el-button>
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
      goodslist: []
    }
  },
  created () {
    this.getGoodsList()
  },
  methods: {
    getGoodsList () {
      this.goodslist = [
        {
          goods_name: '奥利奥',
          goods_price: '20',
          goods_weight: 1,
          add_time: '2020-12'
        },
        {
          goods_name: 'apple',
          goods_price: '2',
          goods_weight: 1,
          add_time: '2020-12'
        },
        {
          goods_name: 'banana',
          goods_price: '6',
          goods_weight: 1,
          add_time: '2020-12'
        },
        {
          goods_name: 'apple',
          goods_price: '2',
          goods_weight: 1,
          add_time: '2020-12'
        },
        {
          goods_name: 'banana',
          goods_price: '6',
          goods_weight: 1,
          add_time: '2020-12'
        },
        {
          goods_name: 'apple',
          goods_price: '2',
          goods_weight: 1,
          add_time: '2020-12'
        },
        {
          goods_name: 'banana',
          goods_price: '6',
          goods_weight: 1,
          add_time: '2020-12'
        }
      ]
    },
    goAddpage () {
      this.$router.push('/goods/add')
    }
  }
}
</script>
<style lang="less" scoped>
.cat_opt {
  margin: 15px;
}
</style>
