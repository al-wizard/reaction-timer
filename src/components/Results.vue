<template>
    <div class="results">
      <h3 :class="classs">Реакция: {{ score }} милисекунд!</h3>
      <p :class="classs">Вердикт: {{ rank }} </p>        
    </div>

</template>

<script>
   export default {
       props: ['score'],
       data() {
           return {
               rank: null,
               classs: null
           }
       },
       mounted() {
           if(this.score < 350) {
               this.rank = 'пальцы ниндзи..!'
               this.classs = 'green'
           } else if(this.score < 400) {
               this.rank ='хорошие рефлексы!'
               this.classs = 'brown'
           } else {
               this.rank = 'медленновато будет...'
               this.classs = 'red'
           }
       }
   }
    
</script>

<style scoped>
    .results {
        border: 1px dotted grey;
        border-radius: 10px;
        padding: 15px;
    } 
    .green { color: green }
    .brown { color: brown }
    .red { color: red }        
</style>