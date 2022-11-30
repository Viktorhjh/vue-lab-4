
<template>
  <div id="main">    
      <div>
        <InputUser @error="showError" isNumber = 0 minCountCharackters = 3>Name</InputUser>
      </div>
      <div>
        <InputUser @error="showError" isNumber = 0 minCountCharackters = 3>Surname</InputUser> 
      </div>
      <div>
         <InputUser @error="showError" isNumber = 1 minCountCharackters = 2 minVal= 0> Age</InputUser> 
      </div>
      <div>      
        <InputUser @error="showError" isNumber = 2 minCountCharackters = 5>Adress</InputUser> 
      </div>
  </div>
</template>

<script>
import InputUser from './components/Input.vue'
  export default{
    name: 'App',
    components: {
      InputUser
    },
    data(){
    return{            
        };
    },
    methods: {
      showError(str){
        alert(str)
      }
    }
  }
  

</script>

<style scoped>
  #main{
    padding: 10px;    
    text-align: center;
    padding-top: 200px;
  }

</style>
