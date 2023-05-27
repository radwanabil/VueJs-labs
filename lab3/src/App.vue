<template>
<div>

<button class="btn px-2 mr-5 btn-space mt-2 bg-light">
    <span class="button-content" @click="toggleForm">Form</span>
</button>
<button class="btn px-2 mr-5 btn-space mt-2 bg-light"  @click="toggleAdmin"><span class="button-content">Admin</span></button>
<button class="btn px-2 mr-5 btn-space mt-2 bg-light" @click="toggleStudent"><span class="button-content">Students</span></button>
<formParent v-if="showForm" @addingNewAdmin="adminAdded" @addingNewStudent="studentAdded" />
<adminChild :admins="admins" v-if="showAdmin" @deletingAdmin="deleteAdmin" />
<studentChild :students="students" v-if="showStudents" @deletingStudent="deleteStudent" />
</div>
</template>

<script>
import formParent from './components/Form.vue';
import adminChild from './components/Admin.vue';
import studentChild from './components/Student.vue';
import { ref } from 'vue';
export default (await import('vue')).defineComponent ({
  name: 'App',
  components:{
    formParent,
    adminChild,
    studentChild,
    
  },
  setup(){
    const showForm = ref(true)
    const showAdmin = ref(false)
    const showStudents = ref(false)
    const admins = ref([
        {
          name: 'Radwa',
          age: 24,
       
        }
      ])
    const students = ref([
        {
          name: 'Rima',
          age: 12,

        }
      ])
    function toggleForm(){
      showForm.value = true
      showAdmin.value = false
      showStudents.value = false
    }
    function toggleAdmin(){
      showForm.value = false
      showAdmin.value = true
      showStudents.value = false

    }
    function toggleStudent(){
      showForm.value = false
      showAdmin.value = false
      showStudents.value = true
    }
    function adminAdded(newAdmin) {
      admins.value.push(newAdmin);
      // console.log(this.admins);
    }
    function studentAdded(newStudent) {
      students.value.push(newStudent);
    }
    function deleteStudent(index) {
      students.value.splice(index, 1);
    }
    function deleteAdmin(index) {
      admins.value.splice(index, 1);
    }
    return{
      showForm,
      showAdmin,
      showStudents,
      admins,
      students,
      toggleForm,
      toggleAdmin,
      toggleStudent,
      adminAdded,
      studentAdded,
      deleteStudent,
      deleteAdmin

    }

  },
  data(){
    return{


    }
  },
  methods: {

   
  }

});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
  background-color: rgb(21, 20, 20);
  height: 100vh;
}
.btn-space{
  margin-right: 6px;
  position: relative;
  overflow: hidden;
  height: 3rem;
  padding: 0 2rem;
  border-radius: 1rem;
  background: #c7c7c7;
  background-size: 400%;
  color: #fff;
  border: none;
  width: 100px;
}
.btn-space:hover::before {
  transform: scaleX(1);
}

.button-content {
  position: relative;
  z-index: 1;
}

.btn-space::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  transform: scaleX(0);
  transform-origin: 0 50%;
  width: 100%;
  height: inherit;
  border-radius: inherit;
  background: linear-gradient(
    82.3deg,
    rgba(150, 93, 233, 1) 10.8%,
    rgba(99, 88, 238, 1) 94.3%
  );
  transition: all 0.475s;
}
@import "~bootstrap/dist/css/bootstrap.css";
</style>
