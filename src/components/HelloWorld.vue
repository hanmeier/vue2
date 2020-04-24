<template>
  <div>
    <el-table :data="data">
      <el-table-column label="省名" prop="provinceShortName"></el-table-column>
      <el-table-column label="确诊人数" prop="confirmedCount"></el-table-column>
      <el-table-column label="死亡人数" prop="deadCount"></el-table-column>
    </el-table>
  </div>
</template>

<script>


  export default {
    name: 'HelloWorld',
    data () {
      return {
        data:[]
      }
    },
    methods:{
      get(){
        let url=this.$HOST
        this.$axios.get('/api')
          .then(response=>{
            this.data= response.data.newslist.map(item=>{
              return{
                "provinceShortName":item.provinceShortName,
                "confirmedCount":item.confirmedCount,
                "deadCount":item.deadCount
              }
            })
            console.log(this.data)
          })
          .catch()
      }
    },
    created(){
      this.get()
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1, h2 {
    font-weight: normal;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
</style>
