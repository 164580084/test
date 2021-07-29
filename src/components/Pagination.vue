<template>
    <div class="hello">
        <button @click="pageClick(-1)">上一页</button>
         <p class="count">{{data.pageIndex}}/{{data.pageSum}}</p>
        <button @click="pageClick(1)">下一页</button>
    </div>
</template>
<script>
export default {
  name: 'Pagination',
  props: {
    msg: String,
    data:{}
  },
  methods:{
      pageClick(i){
        let {pageIndex,pageSum} = this.data
        let count = (pageIndex*1) + i
          if(count < 1){return}
          else if(count > pageSum){return}  
        //不做 节流了
        this.$emit('getData',count)
      }
  }
}
</script>
<style scoped>
.hello{
    display: flex;
    flex-direction: row
}
.count{
 margin:0 10px 0 10px;
 background-color: aquamarine;
}
</style>