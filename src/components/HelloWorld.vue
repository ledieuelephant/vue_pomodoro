<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h4>{{parseInt(seconds / 60)}}:{{parseInt(seconds % 60)}}</h4>
    <button @click="isStarted = false" v-if="isStarted">Stop</button>
    <button @click="isStarted = true" v-else>Start</button>

  </div>
</template>

<script>
export default {
  data(){
    return {
      isStarted : false,
      seconds : 1800,
    }
  },
  methods: {
    refreshTime : function(){
        setInterval(() => {
          if (this.isStarted) {
            this.seconds--
            if (this.seconds <= 0) {
              this.seconds = 0
            }
          }
        }, 1000)
    }
  },
  mounted() {
    this.refreshTime()
  },
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
