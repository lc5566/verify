<template>
  <div id="app">
    <h2>请输入验证码</h2>
    <verify-box  ref="veb"></verify-box>
    <button class="refresh" @click="submit">提交</button>
  </div>
</template>

<script type="text/babel">
  import VerifyBox from '../components/Verify.vue'

export default {
  name: 'app',
  data () {
    return {
    }
  },
  methods : {
    submit:function () {
      this.$refs.veb.submit()
        .then( result => {
          alert( result )
          return this.$refs.veb.submit()
        })
        .catch( err => {
          alert( err )
          return this.$refs.veb.submit()
        })
        .then( result => {
          alert( result )
          axios.post('/user',{
            user : '',
            password : ''
          })
            .then( function (response) {
              console.log( response )
            })
            .catch( function (error) {
              console.log( error )
            })

        })
        .catch( err => {
          alert( err )
        })
    }
  },
  components : {
    VerifyBox
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
  width:500px;
  height:500px;
  border:1px solid #000;
  position: fixed;
  left:0;
  top:0;
  right:0;
  bottom:0;
  margin:auto;
}

h1, h2 {
  font-weight: normal;
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
