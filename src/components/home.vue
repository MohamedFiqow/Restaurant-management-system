<template>
   <Header />
    <h1>Hello user, Welcome on Home Page</h1>
</template>
<script>
import Header from './Header.vue'
import axios from 'axios';
export default{
    name: 'Home',
    components: {
        Header

    },
    async mounted()
    {
        let user= localStorage.getItem( 'user-info');
        this.name= JSON.parse(user).name;
        if(!user)
        {
            this.$router.push({name:'SignUp'})
        }
        let result = axios.get()
    }
  
}
</script>