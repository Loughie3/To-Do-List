<template>

  <div class = 'newGoal' >  {{newGoal.goal}} <button @click ="deleteGoal" >Delete Goal</button>
   
  </div>
</template>

<script>
export default {
    props: ['newGoal'],
    data(){
        return{
            
        }
    },
    methods: {
   deleteGoal() {
    fetch('http://localhost:3000/newGoals.goal' + this.newGoal.id , { method: 'DELETE' })
   }
}
    }
    

</script>

<style>

</style>