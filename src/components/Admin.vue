<template>
    <div>
<table class="table mx-auto w-25 text-dark mt-5 bg-light table-striped">
  <thead>
    <tr>
      <th scope="col">Name</th>
      <th scope="col">Age</th>
      <th scope="col">Action</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="admin, index in admins" :key="admin.name">
      <td>{{admin.name}}</td>
      <td>{{admin.age}}</td>
      <td><button class="btn btn-danger btn-sm" @click="$emit('deletingAdmin', index)">Delete</button></td>
    </tr>
  </tbody>
</table>
    </div>
</template>

<script>
    export default (await import('vue')).defineComponent ({ 
        name:"adminChild",
         props: ['admins'],
    });
</script>

<style scoped>
.table{
    border-radius: 5px;
}

</style>