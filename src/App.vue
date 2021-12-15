<template>
  <div class="app">
    <header>
      <div class="form">
        <input v-model="name" placeholder="Write a username here" /> <br />
        <button @click="handleClick()">Search</button>
      </div>
    </header>
    <LiveWatchedsList :liveWatcheds="liveWatched" v-if="canRender"/>
  </div>
</template>

<script>
import axios from 'axios'
import LiveWatchedsList from './components/LiveWatchedsList.vue'

export default {
  name: 'App',
  components: { LiveWatchedsList },
  data() {
    return {
      name: null,
      liveWatched: null,
      canRender: false
    }
  },
  methods: {
    handleClick() {
      axios
        .get(`http://127.0.0.1:3001/user/${this.name}`)
        .then((res) => {
          const data = res.data.data

          if (data) {
            this.liveWatched = data.liveWatched
            this.canRender = true
          }
        })
        .catch((err) => {
          console.log('failed', err)
        })
    },
  }
}
</script>

<style>
  header {
    text-align: center;
  }
  header .form {
    margin-top: 40px;
  }
  input {
    margin: 10px;
    padding: 8px 16px;
    color: white;
    border: 3px solid #1A1A1A;
    background-color: #1A1A1A;
    border-radius: 0;
    font-weight: bold;
  }
  button {
    margin: 10px;
    color: white;
    border: 3px solid #1A1A1A;
    background-color: #1A1A1A;
    padding: 8px 16px;
    border-radius: 0;
    cursor: pointer;
    font-weight: bold;
  }
</style>
