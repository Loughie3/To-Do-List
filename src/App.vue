<template>
 
<h1>To Do List </h1>
 <addProject />

 
 <div v-for="newGoal in newGoals" :key="newGoal.id" class = 'newGoal'>
  <h2>  <deleteGoal :newGoal = "newGoal" @complete="handleComplete" class = "inLine"  />    </h2> 
  
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
     
},
methods: {
      handleComplete (id) {
        let p = this.newGoals.find(newGoal => {
            return newGoal.id === id
        })
        p.complete = !p.complete
      },
  


  }

}







</script>

<style >
#app 
  {
    width: 650px;
    border-radius: 10px;
    background:black;
    color: bisque;
    text-align: center;
    padding: 40px 0;
    margin: 40px auto;
    

  }
  .newGoal{
    color: crimson;
    text-align: center;
    
    
   
  }
  .inLine {
    display:inline-block
  }
   

</style>
