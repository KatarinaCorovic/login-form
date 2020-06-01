<template>
  <div class="home">

     <div class="form">  
     <div class="left">
       <h1>Login</h1>
      <p>By logging in you agree to the ridicoulously long terms that you didn't botherto read.</p>   
       </div>

     <div class="right">

     
      <label for="email" id="labelEmail">Email</label>
       <input id="email" v-model="inputEmail" type="text">
      
       <label for="pass">Password</label><button class="visibility" v-on:click="changeVisibility">x</button>
       <!-- <i class="fa fa-eye" aria-hidden="true"></i> -->
       <input id="pass" v-model="inputPass" v-bind:type="visible">


       <div class="error" v-if="hasError">{{ error }}</div>
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
      basicEmail:"katarina@basic.com",
      basicPass:"basic",
      adminEmail:"katarina@admin.com",
      adminPass:"admin",
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
      if(this.inputEmail === this.basicEmail && this.inputPass === this.basicPass) {
        this.$router.push({path:'/basic'});

      } else{
        this.hasError = true;

      }

    },

    validateAdmin:function(){
      if(this.inputEmail === this.adminEmail && this.inputPass === this.adminPass) {
        this.$router.push({path:'/admin'});

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
  height: 430px;
  

  
.left{
  display: inline-block;
  width:290px;
  height:180px;
  background-color: #fff;
  position: relative;
  margin-left: -200px;
  margin-top:120px;
  text-align: left;
  
  // margin-top: 200px;


  h1{
    padding-left:20px;
      padding-top: 10px;
      color:#000;
    
  }
  p{
    font-size:15px;
    padding-left:20px;
    color:#a1aaaa;
  
  }

}

.right{
  width:250px;
  height: 250px;
  background-color: #32475c;
  position: absolute;
  left:800px;
  top:150px;
  border-radius:5px;
   box-shadow: 5px 10px 18px #888888;
 

  label{
    display:inline-block;
    color:#b9c5ce;
    font-size:12px; 
    // padding-top: 30px;
    margin-left:-110px;
    margin-top: 20px;
  }
  #labelEmail{
     margin-left:-150px;

  }
    
   input{
    display:block;
    background-color:#32475c ;
    width:175px;
    height:25px;
    border:none;
    box-shadow: 0px 0px 1px 1px #6a7c89;
    color:#9fa6ad;
    margin-left: 35px;  
    margin-top: 10px;
    
  }
  .visibility{
    
    background-color:#32475c;
    border:none;
    color:#9fa6ad;
    font-weight: bold;
    font-size:15px;
    cursor: pointer;
  }


   .login{
     width:180px;
     height: 40px;
     background-color: #fff;
     border:none;
     margin-top:20px;
     cursor: pointer;
   }

   .error{
     color:#860c0c;
     padding-top:5px;
    //  font-size: 15px;

   }

}
}

}




</style>
