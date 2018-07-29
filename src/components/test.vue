<template>
  <div class="test">
    <input type="text" v-model="newWord"><br/>
  <h1>{{title}}</h1>
  {{subtitle}}
  <p>{{user.firstName}}</p>
  <p>{{user.lastName}}</p>
  <p v-text = "user2.firstName"></p>
  <p v-if="showName">{{user2.lastName}}</p>
  <p v-else="showName">Nobody</p>
  <span v-html = "subtitle"></span>

  <ul>
    <li v-for="word in words">{{word.norwegian}} {{word.english}} {{word.nor_sentence}} {{word.eng_sentence}}</li>
  </ul>
  <button v-on:click="submit">Submit</button>
  <button v-on:click="greet('Hello World!')">Greeting</button></br>
  <input type="text" v-on:keyup="pressKey" v-on:keyup.enter="enterHit"/>
  <hr />
    <label>First Name: </label><input type="text" v-model="user.firstName"></br>
    <label>Last Name: </label><input type="text" v-model="user.lastName">
    <h3>{{fullName}}</h3>
    <h2>{{msg}}</h2>
  </hr>
  </div>
</template>

<script>
  export default{
    name: 'test',
    //component properties
    props: {

        msg: {
          type: String,
          default: 'FooBar'
        }

    },

    data() {
      return{
      title: 'Hello World',
      subtitle: '<h1>Hello Again!</h1',
      newWord: '',

      user: {
        firstName: "Beth",
        lastName: "Salvatore"
      },

        user2: {
          firstName: "Mike",
          lastName: "Patterson"
        },

        showName: true,
        //array named items
        words: [{norwegian: 'kylling'},
                {english: 'chicken'},
                {nor_sentence: 'Du har kylling lepper!'},
                {eng_sentence: 'You have chicken lips!'}
        ]
      }
    },
      methods:{
        submit: function(){
          alert("Your form has been submitted!");
        },
        // passing parameters
        greet: function(greeting){
          alert(greeting);
        },
        // event
        pressKey: function(e){
          console.log(e.target.value);
        },

        enterHit: function(e){
          console.log('You hit enter');
        }
      },
      // computed methods
      computed: {
        fullName: function(){
          // in the user object
          return this.user.firstName + ' ' + this.user.lastName;
        }
      }
  }
</script>

<style scoped>


</style>
