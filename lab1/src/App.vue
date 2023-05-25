<template>
<div>

<button class="btn px-2 mr-5 btn-space mt-2">
    <span class="button-content" @click="toggleForm">Form</span>
</button>
<button class="btn px-2 mr-5 btn-space mt-2"  @click="toggleAdmin"><span class="button-content">Admin</span></button>
<button class="btn px-2 mr-5 btn-space mt-2" @click="toggleStudent"><span class="button-content">Students</span></button>
<formParent v-if="showForm" @addingNewAdmin="adminAdded" @addingNewStudent="studentAdded" />
<adminChild :admins="admins" v-if="showAdmin" @deletingAdmin="deleteAdmin" />
<studentChild :students="students" v-if="showStudent" @deletingStudent="deleteStudent" />
</div>
</template>

<script>
import formParent from './components/Form.vue';
import adminChild from './components/Admin.vue';
import studentChild from './components/Student.vue';
export default (await import('vue')).defineComponent ({
  name: 'App',
  components:{
    formParent,
    adminChild,
    studentChild,
    
  },
  data(){
    return{
     admins: [
        {
          name: 'Radwa',
          age: 24,
       
        }
      ],
      students: [
        {
          name: 'Rima',
          age: 12,

        }
      ],
      showForm: true,
      showAdmin: false,
      showStudent: false,
    }
  },
  methods: {

    toggleForm(){
    this.showForm = true;
    this.showAdmin = false;
    this.showStudent = false;
    },
    toggleAdmin(){
      this.showAdmin = true;
      this.showForm = false;
      this.showStudent = false;

    },
    toggleStudent(){
      this.showForm = false;
      this.showStudent = true;
      this.showAdmin = false;
    },
    adminAdded(newAdmin) {
      this.admins.push(newAdmin);
      console.log(this.admins);
    },
    studentAdded(newStudent) {
      this.students.push(newStudent);
    },
    deleteStudent(index) {
      this.students.splice(index, 1);
    },
    deleteAdmin(index) {
      this.admins.splice(index, 1);
    },
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
  background: #3d3a4e;
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
