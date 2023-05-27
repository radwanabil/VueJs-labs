<template>
<div class="form-box mx-auto mt-5">
<form class="form" @submit.prevent="addUser" ref="form">
    <span class="title">Sign up</span>
    <div class="form-container">
      <input type="text" ref="nameInput" class="input" placeholder="Name" v-model="name">
			<input type="text" class="input" placeholder="Age" v-model.number="age">
 <div class="form-check w-25 mt-2">
                    <input class="form-check-input" type="radio" name="role" value="admin" v-model="role" checked />
                    <label class="form-check-label" for="Admin"> Admin </label>
                </div>
                <div class="form-check w-25 mt-2">
                    <input class="form-check-input" type="radio" name="role" value="student" v-model="role" />
                    <label class="form-check-label" for="Student"> Student </label>
                </div>
    </div>
    <button type="submit">Sign up</button>
</form>
</div>
</template>

<script>
    import { ref, onMounted } from 'vue'
    export default {
        name: 'formParent',
        setup(props,context){
          const name = ref(' ')
          const age = ref(0)
          const role = ref('admin')
          const nameInput = ref(null)
          onMounted(() => {
            nameInput.value.focus()
        })
         function addUser() {
            if (role.value == 'admin') {
                context.emit('addingNewAdmin', { 'name': name.value, 'age': age.value})
            } else {
                context.emit('addingNewStudent', { 'name': name.value, 'age': age.value})
            }
            name.value = ' '
            age.value = 0
            role.value = 'admin'
         }
          return {
            name,
            age,
            role,
            nameInput,
            addUser
        }
        },
    data(){
        return{
            
        }
        },
        methods:{
            
        }
    }
    
</script>

<style scoped>
.form-box {
  max-width: 300px;
  background: #f1f7fe;
  overflow: hidden;
  border-radius: 16px;
  color: #010101;
}

.form {
  position: relative;
  display: flex;
  flex-direction: column;
  padding: 32px 24px 24px;
  gap: 16px;
  text-align: center;
}

/*Form text*/
.title {
  font-weight: bold;
  font-size: 1.6rem;
}


/*Inputs box*/
.form-container {
  overflow: hidden;
  border-radius: 8px;
  background-color: #fff;
  margin: 1rem 0 .5rem;
  width: 100%;
}

.input {
  background: none;
  border: 0;
  outline: 0;
  height: 40px;
  width: 100%;
  border-bottom: 1px solid #eee;
  font-size: .9rem;
  padding: 8px 15px;
}

.form-section {
  padding: 16px;
  font-size: .85rem;
  background-color: #e0ecfb;
  box-shadow: rgb(0 0 0 / 8%) 0 -1px;
}


/*Button*/
.form button {
  background-color: #286cd4;
  color: #fff;
  border: 0;
  border-radius: 24px;
  padding: 10px 16px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: background-color .3s ease;
}

.form button:hover {
  background-color: #005ce6;
}
</style>