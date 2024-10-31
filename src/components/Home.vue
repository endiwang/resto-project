<template>
    <Header />
    <h1>Hello {{ name }}, Welcome on Homepage</h1>
    <table border="1">
        <thead>
            <tr>
                <td>ID</td>
                <td>Name</td>
                <td>Contact</td>
                <td>Address</td>
                <td>Action</td>
            </tr>
        </thead>
        <tr v-for="item in restaurant" :key="item.id">
            <td>{{ item.id }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.contact }}</td>
            <td>{{ item.address }}</td>
            <td>
                <router-link :to="'/update/' + item.id">Update</router-link>
                <button v-on:click="deleteRestaurant(item.id)">Delete</button>
            </td>
        </tr>
    </table>
</template>
<script>
import Header from './Header.vue'
import axios from 'axios';
export default {
    name: "HomePage",
    data() {
        return {
            name: '',
            restaurant: [],
        }
    },
    components: {
        Header
    },
    methods:
    {
        async deleteRestaurant(id) {
            
            let deleteData = await axios.delete("http://localhost:3000/restaurant/" + id);
            console.warn(deleteData)
            if (deleteData.status == 200) {
                // this.loadData();
                let result = await axios.get("http://localhost:3000/restaurant");
            
                this.restaurant = result.data;
            }
        },
        async loadData() {
            let user = localStorage.getItem('user-info');
            console.log('user',user);
            this.name = JSON.parse(user).name;
            if (!user) {
                this.$router.push({ name: 'SignUp' })
            }

            
        }
    },
    async mounted() {
        // this.loadData();
        let result = await axios.get("http://localhost:3000/restaurant");
            console.warn(result)
            this.restaurant = result.data;
        

    }
}
</script>

<style>
td {
    width: 160px;
    height: 40px;

}
</style>