<template>
 
 

  <nav>
    <div>Home</div>
    <div>About</div>
    <div>Blog</div>
    <div>Contect</div>
  </nav>
  <h1><center>Todo Application</center></h1>

  <span class="table">
  <table border>
    <thead>
      <th>ID</th>
      <th>Title</th>
      <th>Description</th>
      <th>Completed</th>
    </thead>
    <!-- <li v-for="(item, index) in items" :key="index">{{ item }}</li> -->
<tbody >
  <!-- <p v-for="(item ,index) in menus" :key="index"> {{ item }} </p> -->
  <tr v-for="(item, index) in menus" :key="index">
    <td> {{ index+1 }} </td>
    <td> {{ item.title }} </td>
    <td> {{ item.desc }} </td>
    <td> {{ item.completed }} </td>
   
    <td> <button  v-on:click="Delete()" data-id="index" style="background-color: red;">Delete</button> </td>

  </tr>
</tbody>
  </table>

<br><br>
  <div class="addData" style="border: 2px solid black;">
    <div>
    <h1><center>Add Item</center></h1>

    
      <!-- <input type="text" name="" id="" placeholder="Enter Your ID" v-model="id"><br> -->
      <input type="text" name="" id="" placeholder="Enter Your Title" v-model="title"><br>
      <input type="text" name="" id="" placeholder="Enter Your Description " v-model="desc"><br>
      <input type="text" name="" id="" placeholder="Enter Your Task Completed (yes/no)" v-model="completed"><br>
      <button v-on:click="store()">Click Me</button>

    </div>

  </div>
  </span>

 
</template>

<script>


export default {
  name: 'HelloWorld',
  data () {
    let x =JSON.parse(localStorage.getItem("data"))
    return {
      menus : x
    }
  },
 
  methods : {
    
    store(){
    //  console.log(this.id)
     let data = JSON.parse(localStorage.getItem("data")) || []
     let item = { title : this.title , desc : this.desc , completed : this.completed}
     data.push(item)

     localStorage.setItem("data" , JSON.stringify(data) )
     console.log(data)
  


    

    },
    Delete(){ 
      console.log()
    }
    

    

    
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


nav{
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  background-color: gray;
  color: rgb(8, 8, 75);
  font-size: 25px;
  font-weight: bold;
  padding: 20px;
}



table{
  width: 40%;
}

.addData{
  width: 40%;
  border: 2px solid black;
  display: flex;
  justify-content:center ;
  

}

.table th{
  padding: 20px;

}

form{
  background-color: rgba(151, 184, 184, 0.477);
  

}
form>input{
  padding: 10px;
  margin: 10px;
}
</style>
