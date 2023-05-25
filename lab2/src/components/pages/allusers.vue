<template>
  <div>
    <h1 class="mb-4">All Users</h1>
    <router-link :to="`/create`" class="btn btn-md btn-info ms-4 mb-3" aria-current="page">Create</router-link>
    <table class="table table-striped text-center w-50 mx-auto table-dark">
  <thead>
    <tr>
      <th scope="col ">#</th>
      <th scope="col">First Name</th>
      <th scope="col">Last Name</th>
      <th scope="col">Actions</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="user in users" :key="user.id">
      <th scope="row">{{ user.id }}</th>
      <td>{{ user.first_name }}</td>
      <td>{{user.last_name}}</td>
      <td>
        <button class="btn btn-sm btn-danger" @click="deleteUser(user.id)">Delete</button>
        <router-link :to="`/users/${user.id}`" class="btn btn-sm btn-primary ms-4">Details</router-link>
        <router-link :to="`/update/${user.id}`" class="btn btn-sm btn-success ms-4">Update</router-link>
      </td>
    </tr>
   
  </tbody>
</table>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "allusersApp",
  created() {
    this.getallusers();
  },
  data() {
    return {
      users: [],
    };
  },
  methods: {
    getallusers() {
      axios
        .get("  http://localhost:2000/users")
        .then((res) => {
          console.log(res.data);
          this.users = res.data
        })
        .catch((err) => console.log(err));
    },
    deleteUser(id){
        axios.delete(`  http://localhost:2000/users/${id}`)
        .then((res)=>{
            console.log(res.data)
            this.getallusers()
        })
        .catch((err)=>console.log(err))
    }
  },
};
</script>

<style scoped>


</style>
