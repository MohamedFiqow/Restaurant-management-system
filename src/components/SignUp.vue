<template>

        <img class="logo" src="../assets/logoResto.png" />
        <h1>Sign Up</h1>
        <div class="register">
        <input type="text" v-model="name" placeholder="Enter Name" />
        <input type="text" v-model="email" placeholder="Enter Email" />
        <input type="text" v-model="password" placeholder="Enter Password" />
        <button v-on:click="SignUp">  Sign Up</button>
        <p>
            <router-link to="/login" >Login </router-link>
        </p>
       
        
         </div>   

    </template>
<script>
import axios from 'axios'
export default {
    name : 'SignUp',
    Data()
    {
return{
    name:'',
    email:'',
    password:'',
}
    },
    methods:{
        async SignUp()
        {
            let result = await axios.post("http://localhost:3000/users",{
                email: this.email, password: this.password, name: this.name
            });
            console.warn(result);
            if(result.status== 201)
            {
              
                localStorage.setItem("user-info", JSON.stringify(result.data))
                this.$router.push({name : 'Home'})
            }
        }

    },
mounted()
    {
        let user= localStorage.getItem( 'user-info');
        if(user)
        {
            this.$router.push({name:'Home'})
        }
    }
    
}
</script>
<style>

/*#container{
  width: 100%;
     height: 100%; 
     display: flex;
    align-items: center;
    justify-content: center; 
     flex-direction:  column;
    overflow: hidden;
}*/

</style>