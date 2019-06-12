<template>
  <div class="hello">
    <button @click="show=!show">按钮</button>
    <!-- <button @click="showq">点我</button> -->
    <table v-if="show" class="asdf" border="1">
      <th>IMEI &nbsp;</th>
      <th>device &nbsp;</th>
      <th>message &nbsp;</th>
      <th>tel &nbsp;</th>
      <th>createdAt &nbsp;</th>
      
      <tr v-for="index in syk">
        
        <!-- <td>{{index.id}}</td> -->
        <td>{{index.IMEI}}</td>
        <td>{{index.device}}</td>
        <td>{{index.message}}</td>
        <td>{{index.tel}}</td>
        <td>{{index.createdAt}}</td>
     
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
          syk:'',
          show:'false'
    }
  },
  created(){
      this.axios.get('http://localhost:60020/all').then((response)=>{
        console.log(response.data.data[1]);
        this.syk=response.data.data;
        console.log(this.syk);
      }).catch((error)=>{
          console.log(error)
      })
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* h3 {
  margin: 40px 0 0;
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
} */
.asdf{
  text-align: center;
  margin: 0 auto;
  /* border: 1px solid */
  margin-top: 15px;

}


</style>
