<template>
<div class="form-box mx-auto mt-5">
<form class="form" @submit.prevent="addUser">
    <span class="title">Sign up</span>
    <div class="form-container">
      <input type="text" class="input" placeholder="Name" v-model="newUser['name']">
			<input type="text" class="input" placeholder="Age" v-model.number="newUser['age']">
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

    export default {
        name: 'formParent',
    data(){
        return{
             newUser: {
                name: '',
                age: '',
            },
            role: 'admin'
        }
        },
        methods:{
            addUser(){
                if (this.role == 'admin') {
                this.$emit("addingNewAdmin", this.newUser)
                
            } else {
                this.$emit("addingNewStudent", this.newUser)
                
            }
            this.newUser = {
                name: '',
                age: '',
            }
            this.role = 'admin'
            }
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