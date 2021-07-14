<template>
  <div>
    <!-- 面包屑导航区 -->
    <el-breadcrumb separator-class="el-icon-arrow-right">
      <el-breadcrumb-item :to="{ path: '/home' }">首页</el-breadcrumb-item>
      <el-breadcrumb-item>信息管理</el-breadcrumb-item>
      <el-breadcrumb-item>信息查询</el-breadcrumb-item>
    </el-breadcrumb>
    <!-- 卡片视图 -->
    <el-card>
      <!-- 搜索 添加 -->
      <el-row :gutter="20">
        <el-col :span="6">
          <el-input placeholder="请输入id" v-model="queryInfo.query_id" clearable @clear="getScoreList">
            <el-button slot="append" icon="el-icon-search" @click="getScoreList"></el-button>
          </el-input>
        </el-col>
          <el-col :span="6">
          <el-input placeholder="请输入服务器名称" v-model="queryInfo.query_cpu" clearable @clear="getScoreList">
            <el-button slot="append" icon="el-icon-search" @click="getScoreList"></el-button>
          </el-input>
        </el-col>

      </el-row>
      <!-- 用户列表区域 -->
      <el-table :data="scorelist" border stripe>
        <!-- stripe: 斑马条纹
        border：边框-->
        <el-table-column type="index" label="#"></el-table-column>
        <el-table-column prop="sys_id" label="id"></el-table-column>
        <el-table-column prop="sys_name" label="服务器"></el-table-column>
        <el-table-column prop="cpu" label="cpu"></el-table-column>
        <el-table-column prop="memory" label="内存"></el-table-column>
        <el-table-column prop="net" label="网络"></el-table-column>
        <el-table-column prop="disk" label="硬盘"></el-table-column>
        <el-table-column label="操作">
          <template slot-scope="scope">
            <el-button
              type="primary"
              icon="el-icon-edit"
              size="mini"
              circle
              @click="showEditDialog(scope.row.id)"
            ></el-button>
            <el-button
              type="danger"
              icon="el-icon-delete"
              size="mini"
              circle
              @click="removeUserById(scope.row.id)"
            ></el-button>

          </template>
        </el-table-column>
      </el-table>
      <!-- 分页区域 -->
      <el-pagination
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
        :current-page="queryInfo.pagenum"
        :page-sizes="[2, 5, 10, 15]"
        :page-size="queryInfo.pagesize"
        layout="total, sizes, prev, pager, next, jumper"
        :total="totle"
      ></el-pagination>
    </el-card>





  </div>
</template>

<script>
  export default {
    data () {

      return {
        // 获取用户列表查询参数对象
        queryInfo: {
          query_id:'',
          query_cpu:'',
          // 当前页数
          pagenum: 1,
          // 每页显示多少数据
          pagesize: 5
        },
        scorelist: [
          {sys_id:1,sys_name:1,cpu:"i7",memory:"13",net:"100",disk:100}
        ],





      }
    },
    created () {

    },
    methods: {

    }
  }
</script>

<style lang="less" scoped>
</style>
