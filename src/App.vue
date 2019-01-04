<template>
  <div id="app">
    <p>{{content}}</p>
    <button @click='clickToAbout'>to about</button>
    <button @click='clickToHome'>to home</button>
    <router-view></router-view>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        content: '',
        history: []
      }
    },
    methods: {
      clickToAbout() {},
      clickToHome() {}
    },
    mounted() {





      var obj = function() {
        this.eventsArr = {
        };
        this.click = function() {
          this.eventsArr['click'].forEach(item => {
            item();
          })
        };
        this.addEventListener = function(name, callback) {
          if (this.eventsArr[name]) {
            this.eventsArr[name].push(callback)
          } else {
            this.eventsArr[name] = [callback];
          }
        };
      }
      var per1 = new obj();
      var per2 = new obj();
      per1.addEventListener('click', function() {
        console.log('object2');
      });
      per1.addEventListener('click', function() {
        console.log('object1');
      });
       per1.addEventListener('click', function() {
        console.log('object3');
      });
      per1.click();
      console.log('>>>>>>>>>>>>');
       per2.addEventListener('click', function() {
        console.log('ppppppp');
      });
      per2.click();
    }
  };
</script>

<style lang="scss">
  #app {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }
  #nav {
    padding: 30px;
    a {
      font-weight: bold;
      color: #2c3e50;
      &.router-link-exact-active {
        color: #42b983;
      }
    }
  }
</style>
