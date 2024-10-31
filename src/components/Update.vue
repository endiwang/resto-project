<template>
    <Header/>
    <h1>Hello User, Welcome on Update Restaurant Page</h1>
    <form class="update">
        <input type="text" name="name" id="" placeholder="Enter Name" v-model="restaurant.name"/>
        <input type="text" name="address" id="" placeholder="Enter Address" v-model="restaurant.address"/>
        <input type="text" name="contact" id="" placeholder="Enter Contact" v-model="restaurant.contact"/>
        <button type="button" v-on:click="updateRestaurant">Update Restaurant</button>
    </form> 

</template>
<script>
import Header from './Header.vue'
import axios from 'axios';
export default  {
    name: "UpdatePage",
    components:{
        Header
    },
    data()
    {
        return {
            restaurant :{
                name:'',
                address:'',
                contact:''
            }
        }
    },
    methods:{
        async updateRestaurant()
        {
            const result = await axios.put("http://localhost:3000/restaurant/"+this.$route.params.id,{
                name:this.restaurant.name,
                address:this.restaurant.address,
                contact:this.restaurant.contact
            }) ;
            if(result.status == 200)
            {
                this.$router.push({name:'Home'})
            }
            // console.warn(result)
        }
    },
   async mounted()
    {
        let user=localStorage.getItem('user-info');
        if(!user)
        {
            this.$router.push({name:'SignUp'})
        }
        const query = await axios.get('http://localhost:3000/restaurant/'+this.$route.params.id)
        console.warn(query.data)
        this.restaurant = query.data
    }
}
</script>