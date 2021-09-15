<template>
 <img class="logo" src="../assets/resto.png" />
<h1> Login</h1>
<div class="login">
     <input type="text" v-model="email" placeholder="enter email" />
      <input type="password" v-model="password" placeholder="enter password" />
    <button v-on:click="login" >Login</button>
    <p>
        <router-link to="/Sign-up">Sign Up </router-link>
    </p>
</div>
</template>

<script>
import axios from 'axios'
export default {
    name:'Login',
    data ()
    {
        return {
            email:'',
            password:''
        }
    },
    methods:{
        async login(){
            let result = await axios.get(
                `https://db-vuejs.herokuapp.com/users?email=${this.email}&password=${this.password}`
            )
            if(result.status==200 && result.data.length>0){
                localStorage.setItem("user-info",JSON.stringify(result.data[0]))
                this.$router.push({name:'Home'})
            }
        
        }
    }
}
</script>
