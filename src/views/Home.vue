<template>
  <div class="home">
     <el-table :data="list" style="width: 100%">
        <el-table-column prop="id" label="ID">
      </el-table-column>
      <el-table-column prop="birthday" label="出生年月">
      </el-table-column>
       <el-table-column prop="age" label="年龄"></el-table-column>
      <el-table-column prop="name" label="姓名"></el-table-column>
      <el-table-column prop="city" label="城市"></el-table-column>
      <el-table-column prop="image" label="图片">
         <template slot-scope="scope">
            <img  :src="scope.row.image" alt="" style="width: 50px;height: 50px">
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
      list:[]
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
        console.log(res)
        this.list = res.users;
      })
    }
  }
}
</script>
