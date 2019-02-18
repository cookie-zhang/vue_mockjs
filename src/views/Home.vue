<template>
  <div class="home">
    <el-button type="success" @click="getClumInfomation">获取</el-button>
     <el-table :data="list" style="width: 100%" @selection-change="changeFun" >
      <el-table-column type="selection" width="55"></el-table-column>
      <el-table-column prop="id" label="ID"></el-table-column>
      <el-table-column prop="birthday" label="出生年月"></el-table-column>
       <el-table-column prop="age" label="年龄"></el-table-column>
      <el-table-column prop="name" label="姓名"></el-table-column>
      <el-table-column prop="city" label="城市"></el-table-column>
      <el-table-column prop="image" label="图片">
         <template slot-scope="scope">
            <img :src="scope.row.image" alt="" style="width: 50px;height: 50px">
         </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
// @ is an alias to /src
import api from '../axios/api.js'

export default {
  name: 'home',
  data(){
    return{
      list:[],
      multipleSelection:[],
    }
  },
  components: {
  },
  created(){
    this.getList()
  
  },
  methods: {
    getList: function () {
      api.JH_news('/api/list','type=1234')
      .then((res)=>{
        this.list = res.users;
      })
    },
    getClumInfomation: function(val){
      console.log(this.multipleSelection)
    },
    changeFun: function(val){
        this.multipleSelection = val;
    }

  }
}
</script>
