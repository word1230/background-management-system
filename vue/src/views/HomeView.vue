<template>
    <el-container style="min-height: 100vh;">
      <el-aside :width="sideWidth+'px'" style="background-color: rgb(238, 241, 246); min-height: 100%; box-shadow: 2px 0 6px rgba(0, 21, 41, .35);">
        <el-menu :default-openeds="['1', '3']" style="min-height: 100%;overflow: hidden;" 
        background-color="rgb(48,56,86)"
        text-color="#fff"
        active-text-color="#ffd04b"
        :collapse-transition="false"
        :collapse="isCollapse"
         >
         <div style="height: 60px;line-height: 60px; text-align: center;">
            
          <img src="../assets/logo.png" alt="" style="width: 20px;position: relative; top: 5px;margin-right: 5px;">
          <b style="color: #fff;" v-show="logTextShow">后台管理系统</b>
         </div>
          <el-submenu index="1">
            <template slot="title"
              ><i class="el-icon-message"></i>
              <span slot="title">导航一</span>
              </template
            >
            <el-menu-item-group>
              <template slot="title">
               分组一
              </template>
              <el-menu-item index="1-1">选项1</el-menu-item>
              <el-menu-item index="1-2">选项2</el-menu-item>
            </el-menu-item-group>
          
          </el-submenu>
          <el-submenu index="2">
            <template slot="title"><i class="el-icon-menu"></i>
              <span slot="title">导航二</span>
            </template>
            <el-menu-item-group>
              <template slot="title">分组一</template>
              <el-menu-item index="2-1">选项1</el-menu-item>
              <el-menu-item index="2-2">选项2</el-menu-item>
            </el-menu-item-group>
           
          </el-submenu>
          <el-submenu index="3">
            <template slot="title"
              ><i class="el-icon-setting"></i>
              <span slot="title">导航三</span>
              </template
            >
            <el-menu-item-group>
              <template slot="title">分组一</template>
              <el-menu-item index="3-1">选项1</el-menu-item>
              <el-menu-item index="3-2">选项2</el-menu-item>
            </el-menu-item-group>
           
          </el-submenu>
        </el-menu>
      </el-aside>

      <el-container>
        <el-header style=" font-size: 12px ;border-bottom: 1px solid; line-height: 60px; display: flex;">
      
          <div style="flex: 1;font-size: 25px;">
              <span :class="collapseBtnClass" style="cursor: pointer;" @click="collapse"> </span>
          </div>
          <el-dropdown style="width: 80px; cursor: pointer;" >
            <span>王小虎</span> <i class="el-icon-arrow-down" style="margin-left: 5px;"></i>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item>个人信息</el-dropdown-item>
              <el-dropdown-item>退出</el-dropdown-item>
              
            </el-dropdown-menu>
          </el-dropdown>
          
        </el-header>

        <el-main>
          <el-breadcrumb separator="/">
            <el-breadcrumb-item :to="{ path: '/' }">首页</el-breadcrumb-item>
            <el-breadcrumb-item><a href="/">活动管理</a></el-breadcrumb-item>
          
          </el-breadcrumb>

          <div style="margin: 10px 0;">
              <el-input style="width: 200px;" suffix-icon="el-icon-search" placeholder="请输入名称"></el-input>
              <el-input style="width: 200px;" suffix-icon="el-icon-message" placeholder="请输入邮箱" class="ml-5"></el-input>
              <el-input style="width: 200px;" suffix-icon="el-icon-position" placeholder="请输入地址" class="ml-5"></el-input>
              <el-button style="margin-left: 5px ;" type="primary" >搜索</el-button>
          </div>

          <div style="margin:10px 0">
            <el-button type="primary"><i class="el-icon-circle-plus-outline"></i>新增</el-button>
            <el-button type="primary"><i class="el-icon-remove-outline "></i>批量删除</el-button>
            <el-button type="primary"><i class="el-icon-top "></i>导入</el-button>
            <el-button type="primary"><i class="el-icon-bottom "></i>导出</el-button>
          </div>
          

          <el-table :data="tableData" border="" stripe="" header-cell-class-name="headerBg">
            <el-table-column prop="date" label="日期" width="140">
            </el-table-column>
            <el-table-column prop="name" label="姓名" width="120">
            </el-table-column>
            <el-table-column prop="address" label="地址"> </el-table-column>
            <el-table-column label="操作">
              <template >
                <el-button type="success"><i class=" el-icon-edit"></i>编辑</el-button>
                <el-button type="danger"><i class=" el-icon-remove-outline"></i>删除</el-button>
                </el-button>
              </template>
            </el-table-column>
          </el-table>
          <div style="padding: 10px 0;">
            <el-pagination
            
              :page-sizes="[5, 10, 15, 20]"
              :page-size="10"
              layout="total, sizes, prev, pager, next, jumper"
              :total="400">
            </el-pagination>
          </div>

        </el-main>
      </el-container>
    </el-container>

</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "HomeView",
  components: {
    HelloWorld,
  },
  data() {
    const item = {
      date: "2016-05-02",
      name: "王小虎",
      address: "上海市普陀区金沙江路 1518 弄",
    };
    return {
      tableData: Array(10).fill(item),
      collapseBtnClass: "el-icon-s-fold",
      isCollapse: false,
      sideWidth: 200,
      logTextShow: true,
      headerBg: "headerBg",
    };
  },
  methods: {
    collapse() {
      this.isCollapse = !this.isCollapse;
      if (this.isCollapse) {
        this.sideWidth = 64;
        this.collapseBtnClass = "el-icon-s-unfold";
        this.logTextShow = false;
      } else {
        this.sideWidth = 200;
        this.collapseBtnClass = "el-icon-s-fold";
        this.logTextShow = false;
      }
    },
  },
};
</script>

<style>
.headerBg {
  background: #eee !important;
}
</style>
