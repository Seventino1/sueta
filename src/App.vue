<template>
  <input type="text" v-model="userName" placeholder="Name">
  <input type="password" v-model="userPass" placeholder="Password">
  <input type="email" v-model="userEmail" placeholder="email">
  <button @click="sendData"> Отправить</button>
  <p className="error">{{ error }}</p>

  <div v-if="users.length == 0" className="user">
    Пользователь не найден
  </div>
  <div v-else-if="users.length == 1" className="user">
    Users has one element
  </div>
  <div v-else="users.length == 1" className="user">
    Users has one more elements
  </div>

<User v-for="(el, index) in users" :key="index" className="user" :user="el" :index="index" :deleteUser="deleteUser"/>
   
    


</template>

<style scoped>
input {
    display: block;
    margin-bottom: 10px;
    border-radius: 3px;
    border: 1px solid saddlebrown;
    background: #fafafa;
    color: #333;
    outline: none;
}

button {
    border-radius: 5px;
    outline: none;
    padding: 10px 15px;
    background: #98d198;
    color:green;
    cursor: pointer;
    transition: transform 500ms ease;
}

button:hover {
    transform: translateY(-5px);
}

.user {
    padding: 30px 60px;
    background-color: #533636;
  
    color: white;
    width: 400px;
    text-align: center;
}

.user-2 {
    padding: 30px 60px;
    background-color: #c72222;
  
    color: white;
    width: 200px;
    text-align: center;
}
</style>

<script>
import User from './components/User.vue';

export default {
    components: {User},
    data() {
        return {
            users: [],
            error: '',
            userName: '',
            userPass: '',
            userEmail: '',
           
        }
    },
    methods: {
        sendData() {
            if(this.userName == "") {
                this.error = 'Имя не введено';
                return;
            } else if( this.userPass == "") {
                this.error = 'Пароль не введен';
                return;
            } else if(this.userEmail == "") {
                this.error = 'Email не введен';
                return;
            }

            this.error = '';
            this.users.push({
               
                name: this.userName,
                pass: this.userPass,
                email: this.userEmail
            })

        },
        deleteUser(index) {
            this.users.splice(index,1);
        }
    

    }
}
</script>
