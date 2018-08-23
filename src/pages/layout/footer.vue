<template>
  <div class="juese">
    <div class="guanli"><p>角色管理</p></div>
    <div class="conta">
      <div class="left">
        <input placeholder="输入角色名进行查询">
        <ul>
          <li v-for="(item,index) in list" :key="index">默认管理员</li>
          <li>默认管理员</li>
          <li>默认管理员</li>
        </ul>
      </div>
      <div class="right">
        <div class="big"><h3>默认管理员</h3></div>
        <div class="btn">
          <el-button type="text" @click="open5" class="btn1">添加角色</el-button>
          <el-button type="text" @click="open5" class="btn1">编辑角色</el-button>
          <el-button type="text" @click="open5" class="btn1">复制角色</el-button>
          <el-button type="text" @click="open8" class="btn1">删除角色</el-button>
        </div>
        <div class="ele">
            <ul>
              <li>菜单权限</li>
              <li>数据权限</li>
              <li>文档权限</li>
              <li>用户列表</li>
            </ul>
            <div class="thre">
              <el-tree
                  :data="data2"
                  show-checkbox
                  default-expand-all
                  node-key="id"
                  ref="tree"
                  highlight-current
                  :props="defaultProps">
                </el-tree>
            </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Element from "element-ui";
  export default {
    data(){
      return{
        list:[]
      }
    },
    methods:{
      add(){
        alert(111)
      },
      bian(){
        alert(111)
      },
      copy(){
        alert(111)
      },
      dele(){
        alert(111)
      }
    },
    created:function(){
       var that=this;
       this.$http.get("http://api.haomo-studio.com/org/user_roles").then(function(res) {
          that.list=res.data;
          console.log(this.res.data)
        }) 
    },
    methods: {
      open5() {
        this.$confirm('角色', '添加角色', {
          distinguishCancelAndClose: true,
          confirmButtonText: '取消',
          cancelButtonText: '确定'
        })
          .then(() => {
            this.$message({
              type: 'info',
            });
          })
          .catch(action => {
            this.$message({
              type: 'info',
              message: action === 'cancel'
                
            })
          });
      },
      open8() {
        this.$confirm('确定删除角色', '删除角色', {
          distinguishCancelAndClose: true,
          confirmButtonText: '取消',
          cancelButtonText: '确定'
        })
          .then(() => {
            this.$message({
              type: 'info',
            });
          })
          .catch(action => {
            this.$message({
              type: 'info',
              message: action === 'cancel'
                
            })
          });
      },
      getCheckedNodes() {
        console.log(this.$refs.tree.getCheckedNodes());
      },
      getCheckedKeys() {
        console.log(this.$refs.tree.getCheckedKeys());
      },
      setCheckedNodes() {
        this.$refs.tree.setCheckedNodes([{
          id: 5,
          label: '二级 2-1'
        }, {
          id: 9,
          label: '三级 1-1-1'
        }]);
      },
      setCheckedKeys() {
        this.$refs.tree.setCheckedKeys([3]);
      },
      resetChecked() {
        this.$refs.tree.setCheckedKeys([]);
      }
    },

    data() {
      return {
        data2: [{
          id: 1,
          label: '基础数据',
          children: [{
            id: 4,
            label: '客户',
            
          },{
            id: 9,
            label: '产品',
          }]
        }, {
          id: 2,
          label: '业务申请',
          children: [{
            id: 5,
            label: '项目报备单'
          }, {
            id: 6,
            label: '合同申请单'
          }]
        }, {
          id: 3,
          label: '业务管理',
          children: [{
            id: 7,
            label: '二级 3-1'
          }, {
            id: 8,
            label: '二级 3-2'
          }]
        },{
          id: 4,
          label: '业务申请',
          children: [{
            id: 5,
            label: '项目报备单'
          }, {
            id: 6,
            label: '合同申请单'
          }]
        }, {
          id: 3,
          label: '业务管理',
          children: [{
            id: 5,
            label: '二级 3-1'
          }, {
            id: 8,
            label: '二级 3-2'
          }]
        },
        {
          id: 6,
          label: '业务申请',
          children: [{
            id: 5,
            label: '项目报备单'
          }, {
            id: 6,
            label: '合同申请单'
          }]
        }, {
          id: 7,
          label: '业务管理',
          children: [{
            id: 7,
            label: '二级 3-1'
          }, {
            id: 8,
            label: '二级 3-2'
          }]
        }],
        defaultProps: {
          children: 'children',
          label: 'label'
        }
      };
    }
  }
  
</script>
<style>
  .juese{
    width:935px;
    
    background:#fff;
  }
  .guanli{
    width:932px;
    height:50px;
    color: #797979;
  }
.guanli p{
    width:875px;
    height:30px;
    font-size: 14px;
    text-transform: uppercase;
    font-weight: 600;
    padding-top:15px;
    padding-left:15px;
  }
  .conta{
    width:932px;
    height:540px;
    margin-top:15px;
  }
  .left{
    width:200px;
    height:500px;
    margin-left:15px;
    border-right:1px solid #333;
    float:left;
  }
  .left input{
    background-color: #fafafa;
    color: rgba(0,0,0,0.6);
    font-size: 14px;
    width: 100%;
    height: 34px;
    padding: 6px 12px;
  }
  .left ul{
    width:200px;
    list-style:none;
  }
  .left ul li{
    width:100%;
    height:30px;
    cursor: pointer;
    padding: 6px 12px;
  }
  .left ul li:hover{
    background:#797979;
  }
  .right{
    width:700px;
    height:500px;
    margin-left:230px;
  }
  .big{
    width:664px;
    height:30px;
    font-size:25px;
  }
  .btn{
    width:100%;
    height:50px;
    margin-top:15px;
    margin-left:15px;

  }
  .btn .btn1{
    width:100px;
    height:34px;
    border:1px solid;
    border-color:#ccc;
    font-weight: 400;
    font-size: 14px;
    color:#333;
    border-shadow:5px;
  }
  .ele{
    width:664px;
    margin-left:15px;
  }
  .ele ul{
    width:100%;
    height:32px;
    margin-left:15px;
    list-style:none;
    border-bottom:1px solid #333;
  }
  .ele ul li{
    width:92px;
    height:28px;
    float:left;
    text-align:center;
  }
  .ele ul li:hover{
    background:#eee;
  }
</style>
