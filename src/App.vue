<template>
 
<h1>To Do List </h1>
 <addProject />

 
 <div v-for="newGoal in newGoals" :key="newGoal.id" class = 'newGoal'>
 <li> <deleteGoal :newGoal = "newGoal"/> </li>
 
 
 </div>
 
 

 
</template>


<script>
import addProject from './components/addProject.vue';
import deleteGoal from './components/deleteGoal.vue';



export default {
  name: 'App',
  components: { addProject, deleteGoal },
  data(){
    return {
      newGoals: [],
      
          }
    },
   

    
  
  
  mounted() {
      fetch('http://localhost:3000/newGoals')
      .then(res => res.json())
      .then(data => this.newGoals = data)
      .catch(err => console.log(err.message))
      
}, 
updated(){
  fetch('http://localhost:3000/newGoals')
      .then(res => res.json())
      .then(data => this.newGoals = data)
     
}


}




</script>

<style >
#app 
  {
    width: 400px;
    border-radius: 20px;
    background:crimson;
    color: black;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;

  }
  .newGoal{
    color: bisque;
    text-align: center;
    
    
   
  }
   

</style>
