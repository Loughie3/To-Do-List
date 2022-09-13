<template>
 <form @submit.prevent="handleSubmit">
   <h3><div class= instructions >Type in your goal for the day</div></h3>
  <input type="text" v-model="goal" placeholder="Your goal">
  <input type="submit" value="Add Goal" @click="storeGoal" >
  </form>
</template>


<script>

export default {
  data (){
    return{
      goal: "",
      
    
    }
    
    },
    methods: {
      handleSubmit(){
        let project = {
          goal: this.goal
          }
    
       fetch('http://localhost:3000/newGoals', {
        method: 'POST',
        headers: { 'Content-Type' : 'application/json' },
        body: JSON.stringify(project)
       
       })
      }
    }
  }
  
</script>

<style>
  form {
    max-width: 420px;
    margin: 30px auto;
    background:crimson;
    text-align: left;
    padding: 30px;
    border-radius: 5px;
  }
  .storedGoals {
    color: wheat;
    size: 20px;

  }
  
  
  

  button {
    background:black;
    border: 0;
    padding: 5px 5px;
    margin-top: 10px;
    color: white;
    border-radius: 5px;
  }
  
  
</style>