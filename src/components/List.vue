<template>
  <div class="hello">
     <img :src='data.identityCardUrl' alt="">
     <div>
         <p>{{data.userName}}</p>
         <p>{{data.address}}</p>
     </div>
  </div>
</template>

<script>
export default {
  name: 'List',
  props: {
    msg: String,
    data:[]
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello{
    display: flex;
    flex-direction: row
}
</style>
