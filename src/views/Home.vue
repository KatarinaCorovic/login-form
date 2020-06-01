<template>
  <div class="home">

     <div class="form">  
     <div class="left">
       <h1>Login</h1>
      <p>By logging in you agree to the ridicoulously long terms that you didn't botherto read.</p>   
       </div>

     <div class="right">

     
      <label for="email">Email</label>
       <input id="email" v-model="inputEmail" type="text">
      
       <label for="pass">Password</label><button v-on:click="changeVisibility">x</button>
       <input id="pass" v-model="inputPass" v-bind:type="visible">


       <div v-if="hasError">{{ error }}</div>
       <button class="login" v-on:click="validate">Log in</button>
       </div>
       </div>

    

    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  data:function(){
    return{
      email:"katarina@hehe.com",
      pass:"secret",
      inputEmail:"",
      inputPass:"",
      visible: "password",
      error:"The credentials are not correct.",
      hasError: false
    }
  },
  methods:{
    changeVisibility: function(){
      if(this.visible === "password") {
        this.visible = "text";
      }else {
        this.visible = "password";
      }

    },
    validate:function(){
      if(this.inputEmail === this.email && this.inputPass === this.pass) {
        this.$router.push({path:'/about'});

      } else{
        this.hasError = true;

      }

    }
  }
}
</script>

<style lang="scss" scoped>


body{
  margin:0;
  padding:0;


.home{

  width:900px;
  margin: 0 auto;
  background-color: #dfe0e3;
  height: 400px;
  

  
.left{
  display: inline-block;
  width:290px;
  height:180px;
  background-color: #fff;
  position: relative;
  margin-left: -50px;
  margin-top:100px;
  text-align: left;
  
  // margin-top: 200px;


  h1{
    padding-left:20px;
      padding-top: 20px;
      color:#000;
    
  }
  p{
    font-size:12px;
    padding-left:20px;
    color:#a1aaaa;
  
  
  }

}

.right{
  width:240px;
  height: 240px;
  background-color: #32475c;
  position: absolute;
  left:800px;
  top:150px;
  border-radius:5px;
   box-shadow: 5px 10px 18px #888888;
 

  label{
    color:#6a7c89;
    font-size:12px; 
    display:inline-block;
    
    
  }

  input{
    background-color:#32475c ;
    border:none;
    color:#9da6ad;
    margin-top:20px;
 

  }

   #email{
     margin-top:30px;
   } 

   #pass{
     margin-top:50px;


   }

   .login{
     width:170px;
     height: 40px;
     background-color: #fff;
     border:none;
     margin-top:50px;
   }

}

}
}



</style>
