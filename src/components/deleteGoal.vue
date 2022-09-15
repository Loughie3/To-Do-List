<template>

  <div class = 'newGoal' :class = "{complete: newGoal.complete}"> - {{newGoal.goal}} <button @click ="deleteGoal" >Delete Goal</button>  <button @click = "toggleComplete"> Completed </button>
    
  </div>
  
  
</template>

<script>
export default {
    props: ['newGoal'],
    data(){
        return{

            uri: 'http://localhost:3000/newGoals/' + this.newGoal.id 
        }
    },
    methods: {
   deleteGoal() {
    fetch(this.uri, { method: 'DELETE' })
   },
   toggleComplete (){
        console.log("goal Completed ")
        fetch(this.uri, { 
        method: 'PATCH',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ complete: !this.newGoal.complete})
      }).then(() => {
        this.$emit('complete', this.newGoal.id )
      }).catch(err => console.log(err))
}
    

    }
}
    

</script>

<style>

.newGoal.complete{
    color:rgb(118, 192, 8);
    text-decoration: line-through; 
    text-decoration-color: bisque;
    text-decoration-thickness: 3px;
}

    



</style>