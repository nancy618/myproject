<template>
  <div>
    <!-- 面包屑导航区域 -->
    <el-breadcrumb separator-class="el-icon-arrow-right">
      <el-breadcrumb-item :to="{ path: '/home' }">首页</el-breadcrumb-item>
      <el-breadcrumb-item>商品管理</el-breadcrumb-item>
      <el-breadcrumb-item>商品分类</el-breadcrumb-item>
    </el-breadcrumb>
    <!-- 卡片视图 -->
    <el-card>
      <el-row>
        <el-col>
          <el-button type="primary">添加分类</el-button>
        </el-col>
      </el-row>
    </el-card>
  </div>
</template>
<script>
export default {
  data () {
    return {
      // 查询条件
      querInfo: {
        type: 3,
        pagenum: 1,
        pagesize: 5
      },
      // 控制添加分类对话框的显示与隐藏
      addCateDialogVisible: false,
      // 添加分类的表单数据对象
      addCateForm: {
        // 将要添加的分类的名称
        cat_name: '',
        // 父级分类的Id
        cat_pid: 0,
        // 分类的等级，默认要添加的是1级分类
        cat_level: 0
      },
      // 添加分类表单的验证规则对象
      addCateFormRules: {
        cat_name: [
          { required: true, message: '请输入分类名称', trigger: 'blur' }
        ]
      },
      // 父级分类的列表
      parentCateList: [],
      // 指定级联选择器的配置对象
      cascaderProps: {
        value: 'cat_id',
        label: 'cat_name',
        children: 'children'
      },
      // 选中的父级分类的Id数组
      selectedKeys: []
    }
  },
  // 点击按钮，展示添加分类的对话框
  showAddCateDialog () {
    // 先获取父级分类的数据列表
    this.getParentCateList()
    // 再展示出对话框
    this.addCateDialogVisible = true
  },
  // 获取父级分类的数据列表
  async getParentCateList () {
    const { data: res } = await this.$http.get('categories', {
      params: { type: 2 }
    })

    if (res.meta.status !== 200) {
      return this.$message.error('获取父级分类数据失败！')
    }

    console.log(res.data)
    this.parentCateList = res.data
  },
  // 选择项发生变化触发这个函数
  parentCateChanged () {
    console.log(this.selectedKeys)
    // 如果 selectedKeys 数组中的 length 大于0，证明选中的父级分类
    // 反之，就说明没有选中任何父级分类
    if (this.selectedKeys.length > 0) {
      // 父级分类的Id
      this.addCateForm.cat_pid = this.selectedKeys[
        this.selectedKeys.length - 1
      ]
      // 为当前分类的等级赋值
      this.addCateForm.cat_level = this.selectedKeys.length
    } else {
      // 父级分类的Id
      this.addCateForm.cat_pid = 0
      // 为当前分类的等级赋值
      this.addCateForm.cat_level = 0
    }
  },
  // 点击按钮，添加新的分类
  addCate () {
    this.$refs.addCateFormRef.validate(async valid => {
      if (!valid) return
      const { data: res } = await this.$http.post(
        'categories',
        this.addCateForm
      )

      if (res.meta.status !== 201) {
        return this.$message.error('添加分类失败！')
      }

      this.$message.success('添加分类成功！')
      this.getCateList()
      this.addCateDialogVisible = false
    })
  },
  // 监听对话框的关闭事件，重置表单数据
  addCateDialogClosed () {
    this.$refs.addCateFormRef.resetFields()
    this.selectedKeys = []
    this.addCateForm.cat_level = 0
    this.addCateForm.cat_pid = 0
  }
}

</script>
<style lang="less" scoped></style>
