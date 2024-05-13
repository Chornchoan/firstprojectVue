<template>
  <div class="container">
<div class="header w-250 ">
        <h1 class="d-grid gap-2 col-3 mx-auto mt-5" >Tables</h1>
          <div>
            <input type="text" v-model="newUser.firstname" placeholder="FirstName">
            <input type="TEXT" v-model="newUser.lastname" placeholder="LastName">
            <input type="email" v-model="newUser.email" placeholder="Email">
            <button class="btn btn-primary" v-if="newUsers in newUser !== 0" @click="addUser">Add User</button>
        </div>
        <h4 class="mt-4 text-danger" > Here is totalUsers:{{totalUsers}}</h4>

        <table class="table mb-4">
          <thead class="bg-primary"> 
            <tr>
              <th>ID</th >
              <th>FirstName</th>
              <th>LastName</th>
              <th>Email</th>
            </tr>
          </thead>
          <tbody>
            <tr class="border-colab" v-for="user in users" :key="user.id">
              <td>{{ user.id }}</td >
              <td>{{ user.firstname }}</td>
              <td>{{ user.lastname }}</td>
              <td>{{ user.email }}</td>
              <td>
               <button class="btn btn-danger" @click="deleteUser(user.id)">Delete</button>
              </td>
            </tr>
          </tbody>
        </table> 
      </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: [
        {
          id: 1,
          firstname: 'John',
          lastname: 'Doe',
          email: 'john@gmail.com',
        },
      ],
      newUser: {
        id: null,
        name: '',
        email: ''
      }
    };
  },
  computed: {
    totalUsers: function() {
      return this.users.length;
    }
   
  },
  methods: {
    addUser() {
      this.users.push(this.newUser);
      this.newUser = {
        id: null,
        name: '',
        email: ''
      };
      this.newUser.id = this.users.length +1;
    },
     deleteUser(id) {
    this.users = this.users.filter(user => user.id!== id);
    }
  }
  
  
};
</script>