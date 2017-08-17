<template>
  <div id="app">
    <main>
      <!-- 左侧导航 -->
      <div class="main-left">
        <el-input placeholder="请输入关键字" v-model="filterText">
        </el-input>   <!-- 搜索框 -->
        <!-- 侧边栏 -->
        <el-tree class="filter-tree" :data="data2" :props="defaultProps" default-expand-all :filter-node-method="filterNode" ref="tree2">
        </el-tree>    
      </div>
      <!-- 右侧主内容区 -->
      <div class="main-right">
        1234
        <!-- <transition name="fade">
                              <router-view class="view"></router-view>
                            </transition> -->
      </div>
  
    </main>
  </div>
</template>

<script>

import Vue from 'vue'
import Element from 'element-ui'
import 'element-ui/lib/theme-default/index.css'
import $ from 'jquery'

Vue.use(Element)

export default {
  name: 'app',
  data: function () {
    return {
      active: true,
      headerFixed: true,
      filterText: '',
      data2: [{
        id: 1,
        label: '易学车后台管理系统',
        children: [
          {
            label: '登录'
          },
          {
            id: 2,
            label: '学员端管理',
            children: [{
              id: 3,
              label: '学员信息概览',
              children: [{
                label: '个人信息详情',
              }, {
                label: '代理详情',
              }, {
                label: '审核管理',
              }, {
                label: '学院卡券明细',
              }, {
                label: '课程报名管理',
              }]
            },
            {
              id: 4,
              label: '约考管理',
              children: [{
                label: '约考记录'
              }, {
                label: '考试发布'
              }, {
                label: '题库管理'
              }]
            }
            ]
          },
          {
            id: 5,
            label: '教练端管理',
            children: [{
              id: 6,
              label: '教练信息概览',
              children: [{
                label: '教练信息详情'
              }, {
                label: '设置教练级别'
              }]
            }]
          },
          {
            label: '订单管理'
          },
          {
            label: '佣金设置'
          },
          {
            id: 7,
            label: '广告资讯管理',
            children: [{
              label: '首页banner'
            }, {
              label: '学车指南'
            }]
          },
          {
            id: 8,
            label: '客服管理',
            children: [{
              label: '常见问题'
            }, {
              label: '在线反馈'
            }]
          },
          {
            id: 9,
            label: '财务管理',
            children: [{
              id: 10,
              label: '教练端财务',
              children: [{
                label: '教练提现申请',
              }, {
                id: 11,
                label: '教练返佣统计',
                children: [{
                  label: '教练返佣明细',
                }]
              }]
            }, {
              id: 12,
              label: '学员端财务',
              children: [{
                label: '学员提现申请',
              }, {
                id: 13,
                label: '代理返佣统计',
                children: [{
                  label: '代理返佣明细',
                }]
              }]
            }]
          },
          {
            id: 13,
            label: '系统设置',
            children: [{
              id: 14,
              label: '系统消息列表',
              children: [{
                label: '发送新消息',
              }]
            }, {
              id: 15,
              label: '用户管理',
              children: [{
                label: '新增用户',
              }]
            }, {
              id: 16,
              label: '个人中心',
              children: [{
                label: '密码重置',
              }]
            }]
          },

        ],
      }],
      defaultProps: {
        children: 'children',
        label: 'label'
      }
    };

  },
  created: function () {
    this.$router.push('/activePublic');
  },
  methods: {
    filterNode(value, data) {
      if (!value) return true;
      return data.label.indexOf(value) !== -1;
    }
  },
  watch: {
    '$route': function (to, from) {
      if (to.path == '/activePublic') {
        this.active = true;
      } else if (to.path == '/activeManage') {
        this.active = false;
      }
    },
    filterText(val) {
      this.$refs.tree2.filter(val);
    }
  }
}
</script>

<style>
/* 页面初始化 */
body {
  margin: 0;
}
#app {
  min-width: 1200px;
  margin: 0 auto;
  font-size: 10px;
  font-family: "Helvetica Neue", "PingFang SC", Arial, sans-serif;
}
/* 侧边栏 */
.el-tree-node__content {
    line-height: 24px !important;
    height: 24px !important;
    cursor: pointer;
}




/* 主内容区 */

main {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  min-height: 800px;
  border: solid 10px #E9ECF1;
  background-color: #FCFCFC;
}

main .main-left {
  text-align: center;
  -webkit-box-flex: 0;
  -ms-flex: 0 0 200px;
  flex: 0 0 200px;
}

main .main-right {
  -webkit-box-flex: 1;
  -ms-flex: 1;
  flex: 1;
  background-color: #fff;
  padding: 50px 70px;
}

main .el-menu {
  background-color: transparent!important;
}




/*配置路由*/

.router-link {
  display: inline-block;
  width: 100%;
  height: 100%;
  text-align: center;
  color: #475669;
  text-decoration: none;
}

.is-active .router-link {
  color: #20a0ff;
  /* background-color: red ; */
}











/* 单选框 */

.el-form-item .el-radio+.el-radio {
  margin-left: 30px!important;
}


/* 路由切换动效 */

.fade-enter-active,
.fade-leave-active {
  transition: all .5s;
}

.fade-enter,
.fade-leave-active {
  opacity: 0;
}

.list-enter-active,
.list-leave-active {
  transition: all 1s;
}

.list-enter,
.list-leave-active {
  opacity: 0;
  transform: translateY(30px);
}


/* 导航栏菜单选中效果 */

.isActive {
  color: #20a0ff!important;
}

#app main .aside .is-active {
  color: #475669;
}












/* 卡片 */

.el-card {
  overflow: visible!important;
}
</style>
