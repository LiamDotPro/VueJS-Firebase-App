<template>
  <div id="app">
    <div class="panel-body">
      <table class="table table-striped">
        <thead>
        <tr>
          <th>Title</th>
          <th>Author</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="book in books">
          <td><a v-bind:href="book.url">{{book.title}}</a></td>
          <td>{{book.author}}</td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>

  import Firebase from 'firebase'

  let config = {
    apiKey: 'AIzaSyAB73PEkFZgJBWaxcHAqde5Nb7zjfJI8kg',
    authDomain: 'cyanic-65b0b.firebaseapp.com',
    databaseURL: 'https://cyanic-65b0b.firebaseio.com',
    projectId: 'cyanic-65b0b',
    storageBucket: 'cyanic-65b0b.appspot.com',
    messagingSenderId: '837405215684'
  }

  let app = Firebase.initializeApp(config)
  let db = app.database()
  let booksRef = db.ref('books')

  export default {
    name: 'app',
    data () {
      return {
        newBook: {
          title: '',
          author: '',
          url: 'http://'
        }
      }
    },
    components: {},
    firebase: {
      books: booksRef
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
