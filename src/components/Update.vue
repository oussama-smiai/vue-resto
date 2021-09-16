<template>
<Header/>
<h1>Hello User, Welcome on Update Restaurant Page</h1>
<form class="add">
    <input type="text" name="name" placeholder="Enter Name" v-model="restaurant.name"/> 
    <input type="text" name="address" placeholder="Enter Address" v-model="restaurant.address" /> 
    <input type="text" name="contact" placeholder="Enter Contact" v-model="restaurant.contact"/>
    <button type="button" v-on:click="updateRestaurant">update restaurant</button> 
</form>
</template>
<script>
import Header from './Header.vue'
import axios from 'axios'
export default{
    name: 'Update',
    components:{
        Header
    },
    data(){
        return {
            restaurant :{
                name:'',
                address:'',
                contact:''
            }
        }
    },
    methods:{
        async updateRestaurant(){
            const result =await axios.put("https://db-vuejs.herokuapp.com/restaurant/"+this.$route.params.id, {
                name:this.restaurant.name, 
                address: this.restaurant.address, 
                contact:this.restaurant.contact})
            if(result.status==200)
                this.$router.push({name:'Home'})
        }
    },
    async mounted()
    {
        let user = localStorage.getItem('user-info')
        if (!user){
            this.$router.push({name:'Sign-up'})
        }
        const result = await axios.get('https://db-vuejs.herokuapp.com/restaurant/'+this.$route.params.id)
        this.restaurant=result.data
    }

}
</script>