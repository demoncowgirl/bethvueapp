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

  </div>
</template>

<script>
  export default{
    name: 'test',
    data() {
      return{
      title: 'Hello World',
      subtitle: '<h1>Hello Again!</h1>',
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
          alert("Hello!");
        }
      }
  }
</script>

<style scoped>


</style>
