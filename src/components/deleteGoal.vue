<template>

  <div class = 'newGoal' > {{newGoal.goal}} <button @click ="deleteGoal" >Delete Goal</button>
   
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
   }
}
    }
    

</script>

<style>

</style>