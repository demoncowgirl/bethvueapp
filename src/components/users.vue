<template>
  <div class="users">
    <h1>Users</h1>
    <form v-on:submit="addUser">
      <input type="text" v-model="newUser.name" placeholder="Enter Name"></br>
      <input type="text" v-model="newUser.email" placeholder="Enter Email"></br>
      <input type="submit" value="Submit">
    </form>
    <ul>
      <li v-for="user in users">
        <input type="checkbox" class="toggle" v-model="user.contacted"/>
        <!-- binding to class of contacted -->
        <span :class="{contacted: user.contacted}">
        {{user.name}}: {{user.email}} <button v-on:click="deleteUser(user)">X</button>
      </span>
      </li>
    </ul>
  </div>
</template>

<script>
  export default{
    name: 'users',
    data() {
      return{
        newUser: {},
        users: []
      //     {
      //       name: 'Beth Salvatore',
      //       email: 'bsalvatore@example.com',
      //       contacted: false
      //     },
      //     {
      //       name: 'Mike Patterson',
      //       email: 'steve@example.com',
      //       contacted: false
      //     },
      //     {
      //       name: 'Jane Doe',
      //       email: 'janed@example.com',
      //       contacted: false
      //     },
      //     {
      //       name: 'Ellie Mae',
      //       email: 'em@dogsrus.com',
      //       contacted: false
      //     }
      //   ]
      }
    },
    //
    //     showName: true,
    //     //array named items
    //     words: [{norwegian: 'kylling'},
    //             {english: 'chicken'},
    //             {nor_sentence: 'Du har kylling lepper!'},
    //             {eng_sentence: 'You have chicken lips!'}
    //     ]
    //   }
    // },
      methods:{
        addUser: function(e){
          this.users.push({
            name: this.newUser.name,
            email: this.newUser.email,
            contacted: false
          });
          e.preventDefault();
      },
      deleteUser: function(user){
        // takes user as parameter and deletes only 1
        this.users.splice(this.users.indexOf(user), 1);
      }
    },
    // lifecycle hook
    created: function(){
      this.$http.get('https://jsonplaceholder.typicode.com/users')
      // returns a promise, passes a function
      .then(function(response){
        this.users = response.data;
      });
    }
  }
</script>

<style scoped>
  /* class */
  .contacted{
    text-decoration: line-through;
  }


</style>
