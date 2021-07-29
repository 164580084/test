<template>
  <div id="app">
        <Pagination :data='listData.page' @getData="getData"/>
     <p v-for="(item,i) in  listData.list" :key='i'>
         <List :data='item'/>
     </p>

  </div>
</template>

<script>
import List from './components/List.vue'
import Pagination from './components/Pagination.vue'
import axios from 'axios'
export default {
  name: 'App',
  data(){
    return{
       listData:{page:{},list:[]}
    }
  },
  components: {
    List,
    Pagination
  },
  mounted(){
   this.getData()
  },
  methods:{
    getData(pageIndex){
      let url = `http://yapi.luckly-mjw.cn/mock/50/test/users?pageIndex=${pageIndex?pageIndex:1}`
      axios.get(url)
      .then((response)=>{
        let {data}  = response
        if(data.code == 200){
          if(pageIndex){
            data.data.page.pageIndex =pageIndex
          }
          console.log(data.data)
             this.listData = data.data
             console.log(this.listData)
        }
      })
      .catch(function (error) {
        console.log(error);
      });

    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
