<template>
  <div class="coin-container">
    <div class="coin" v-for="(coin, index) in status" :key="index">
      <p>{{ coin }}</p>
    </div>
  </div>

  <div class="button-container">
    <button @click="toss">Toss</button>
    <button @click="add">Add Coin</button>
    <button @click="remove">Remove Coin</button>
  </div>
  
  <div class="result-container">
    <p>Head: {{ hLength }}</p>
    <p>Tail: {{ tLength }}</p>
    <p>Draw: {{ dLength }}</p>
  </div>
</template>

<script>
// Vue Instance
export default {
  name: 'App',
  data() {
    return {
      status: ['H'] // head
    }
  },
  computed: {
    hLength() {
      return this.status.filter(item => item === 'H').length
    },
    tLength() {
      return this.status.filter(item => item === 'T').length
    },
    dLength() {
      return this.status.filter(item => item === 'D').length
    }
  },
  methods: {
    toss() {
      const hOrT = 'HTD';
      for (let i in this.status) {
        this.status[i] = hOrT[Math.floor(Math.random() * 3)];
      }
    },
    add() {
      this.status.push('H')
    },
    remove() {
      this.status.pop()
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.coin {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: palevioletred;
  width: 3rem;
  height: 3rem;
  margin: 0.5rem;
  border-radius: 1.5rem;
}

.coin p {
  font-weight: bold;
  color: aliceblue;
}

.coin-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 1rem;
}

.button-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 1rem;
}

.button-container button {
  margin: 0.5rem;
  border: none;
  background-color: bisque;
  color: black;
  border-radius: 0.275rem;
  padding: 0.5rem;
}

.result-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 1rem;
}

.result-container p {
  margin: 1rem;
}
</style>
