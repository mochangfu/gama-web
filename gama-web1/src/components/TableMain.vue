<template>
  <div class="layout">
    <Layout >
      <Header  >
        <Menu    class="mymenu" width="100px"  mode="vertical"  active-name="1">

          <div class="layout-nav">
            <MenuItem name="1" >
              导航1
            </MenuItem>
            <MenuItem name="2" >
              导航2
            </MenuItem>
            <MenuItem name="3" >
              导航3
            </MenuItem>
            <MenuItem name="4" >
              导航4
            </MenuItem>
          </div>
        </Menu>
      </Header>
      <Content :style="{padding: '0 100px'}">

        <Card>
          <div style="min-height: 600px;">
            <v-table
              is-horizontal-resize
              style="width:100%"
              :columns="columns"
              :table-data="tableData"
              row-hover-color="#eee"
              row-click-color="#edf7ff"
            ></v-table>
          </div>
        </Card>
      </Content>

    </Layout>
  </div>
</template>

<script>
  export default {
    name: "table-main",
    data() {
      return {
        tableData: [],
        columns: [
          {field: 'id', title: '序号', width: 80, titleAlign: 'center', columnAlign: 'center',isResize:true},
          {field: 'username', title: '用户名', width: 80, titleAlign: 'center', columnAlign: 'center',isResize:true},
          {field: 'realname', title: '姓名', width: 150, titleAlign: 'center', columnAlign: 'center',isResize:true},
          {field: 'nickname', title: '昵称', width: 150, titleAlign: 'center', columnAlign: 'center',isResize:true},
          {field: 'sex', title: '性别', width: 280, titleAlign: 'center', columnAlign: 'left',isResize:true},
          {field: 'telephone', title: '手机', width: 280, titleAlign: 'center', columnAlign: 'left',isResize:true},
          {field: 'qq', title: 'QQ', width: 280, titleAlign: 'center', columnAlign: 'left',isResize:true},
          {field: 'area', title: '地址', width: 280, titleAlign: 'center', columnAlign: 'left',isResize:true}
        ]
      }
    },
    created() {
      //在created函数中使用axios的get请求向后台获取用户信息数据
      this.$ajax('http://localhost:8090/gama/app/findAllUsers').then(res => {
        this.tableData = res.data.data
        console.log(res.data);
      }).catch(function (error) {
        console.log(error);
      });
    }
  }
</script>

<style scoped>
  .layout{
    border: 1px solid #d7dde4;
    background: #f5f7f9;
    position: relative;
    border-radius: 4px;
    overflow: hidden;
    height: 100%;
    margin-left: 20px;
  }
  .layout-nav{
    width: 100px;
    margin: 0 0;
    margin-left: 0px;
  }
  .mymenu{
    margin-top: 65px;
    margin-left: -50px;

  }

</style>
