<template>
 <img class="logo" src="../assets/resto.png" />
<h1> Sign Up6</h1>
<div class="register">
    <input type="text" v-model="name" placeholder="enter name" />
     <input type="text" v-model="email" placeholder="enter email" />
      <input type="password" v-model="password" placeholder="enter password" />
    <button v-on:click="signUp" >Sign Up</button>
    <p>
        <router-link to="/Login">Login </router-link>
    </p>
</div>
</template>
<script>
import axios from 'axios'
export default {
    name :'SignUp',
    data ()
    {
        return {
            name:'',
            email:'',
            password:''
        }
    },
    methods: {
        async signUp(){
            let result = await axios.post("https://db-vuejs.herokuapp.com/users", {email:this.email, password: this.password, name:this.name});
            
        console.warn(result);
        if(result.status==201)
            localStorage.setItem("user-info",JSON.stringify(result.data))
            this.$router.push({name:'Home'})
        }
    },
    mounted()
    {
        let user = localStorage.getItem('user-info')
        if (user){
            this.$router.push({name:'Home'})
        }
    }
}
</script>
