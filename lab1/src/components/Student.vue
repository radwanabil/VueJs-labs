<template>
    <div> 
<table class="table mx-auto w-25 text-dark mt-5 bg-light table-striped">
  <thead>
    <tr>
      <!-- <th scope="col">#</th> -->
      <th scope="col">Name</th>
      <th scope="col">Age</th>
      <th scope="col">Action</th>
    </tr>
  </thead>
  <tbody>

    <tr v-for="student, index in students" :key="student.name">
      <!-- <th scope="row">1</th> -->
      <td>{{student.name}}</td>
      <td>{{student.age}}</td>
      <td><button class="btn btn-danger btn-sm" @click="$emit('deletingStudent', index)">Delete</button></td>
    </tr>
  </tbody>
</table>
    </div>
 
</template>

<script>
    export default (await import('vue')).defineComponent ({
        name:"studentChild",
        props: ['students'],
    });
</script>

<style scoped>
.table{
    border-radius: 5px;
}

</style>