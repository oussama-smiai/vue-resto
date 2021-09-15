<template>
 <img class="logo" src="../assets/resto.png" />
<h1> Login4</h1>
<div class="login">
     <input type="text" v-model="email" placeholder="enter email" />
      <input type="password" v-model="password" placeholder="enter password" />
    <button >Login</button>
    <p>
        <router-link to="/Sign-up">Sign Up </router-link>
    </p>
</div>
</template>

<script>
export default {
    name:'Login',
    data ()
    {
        return {
            email:'',
            password:''
        }
    }
}
</script>