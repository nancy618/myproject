<template>
  <div>
    <!-- 面包屑导航区域 -->
    <el-breadcrumb separator-class="el-icon-arrow-right">
      <el-breadcrumb-item :to="{ path: '/home' }">首页</el-breadcrumb-item>
      <el-breadcrumb-item>用户管理</el-breadcrumb-item>
      <el-breadcrumb-item>用户列表</el-breadcrumb-item>
    </el-breadcrumb>
    <!-- 卡片视图 -->
    <el-card>
      <el-row>
        <el-col>
          <el-button type="primary">角色列表</el-button>
        </el-col>
      </el-row>
      <!-- 卡片视图 -->
      <el-table :data="rolelist" border stripe>
        <el-table-column type="index"></el-table-column>
        <el-table-column label="角色名称" prop="roleName"></el-table-column>
        <el-table-column label="角色描述" prop="roleDesc"></el-table-column>
        <el-table-column label="操作" width="300px">
          <!-- <template>
            <el-tag>一级</el-tag>
            <el-tag type="success">二级</el-tag>
            <el-tag type="warning">三级</el-tag>
          </template> -->
          <template>
            <el-button size="mini" type="primary" icon="el-icon-edit"
              >编辑</el-button
            >
            <el-button size="mini" type="danger" icon="el-icon-delete"
              >删除</el-button
            >
            <el-button
              size="mini"
              type="warning"
              icon="el-icon-setting"
              @click="showSetRightDialog(scope.row)"
              >分配权限</el-button
            >
          </template>
        </el-table-column>
      </el-table>
    </el-card>
  </div>
</template>

<script>
export default {
  data () {
    return {
      // 所有角色列表
      rolelist: []
    }
  },
  created () {
    this.getRoleList()
  },
  methods: {
    getRoleList () {
      this.rolelist = [
        {
          roleName: '商品管理',
          roleDesc: 'goods'
        },
        {
          roleName: '商品管理',
          roleDesc: 'goods'
        },
        {
          roleName: '商品管理',
          roleDesc: 'goods'
        },
        {
          roleName: '商品管理',
          roleDesc: 'goods'
        }
      ]
    }
  }
}
</script>
<style lang="less" scoped></style>
