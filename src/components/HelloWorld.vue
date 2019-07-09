<template>
  <div class="hello">
    <h1>Dude, Hello from amplify...{{ msg }}</h1>
    <h2>{{a}} x {{b}} = </h2>
    <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
    <h3>Installed CLI Plugins</h3>
    <ul>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel" target="_blank" rel="noopener">babel</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-eslint" target="_blank" rel="noopener">eslint</a></li>
    </ul>
    <h3>Essential Links</h3>
    <ul>
      <li><a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank" rel="noopener">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
      <li><a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a></li>
    </ul>
    <h3>Ecosystem</h3>
    <ul>
      <li><a href="https://router.vuejs.org" target="_blank" rel="noopener">vue-router</a></li>
      <li><a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a></li>
      <li><a href="https://github.com/vuejs/vue-devtools#vue-devtools" target="_blank" rel="noopener">vue-devtools</a></li>
      <li><a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
    </ul>
    <input type="text" id="input" v-model="mymessage">
    <p>The value of the input is: {{mymessage}}</p>
    <p>The reversed value of the input is: {{reversedMessage}}</p>
    <ul>
	<!--<li v-for="name in names" v-text="name"></li>-->
    </ul>
    <input type="text" id="nameInput" v-model="newName">
    <button v-on:click="addName">Add Name</button>
    <button @click="addName">Add Name this way</button>
    <br>
    <button v-bind:title="title">Hover Over Me</button>
    <button :title="title">Hover Over Me</button>
    <br>
    <button :class="{ 'is-loading': isLoading}" @click="toggleClass">Click Me </button>
    <br>
    <h2>All Tasks</h2>
    <ul>
       <li v-for="task in tasks" v-text="task.description"></li>
    </ul>
    <h2>Incomplete Tasks</h2>
    <ul>
       <li v-for="task in incompleteTasks" v-text="task.description"></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },

  data() {
    return {
      a:'6',
      b:'7',
      mymessage: 'dude',
      names : ['Jayden','Jay'],
      newName : '',
      title : 'Now the title is being set thru js.',
      isLoading: false,
      tasks : [
        { description: 'Talk to accountant', completed: false},
        { description: 'Do eye exam',completed: false},
        { description: 'start the welder', completed: true}
      ]
    }
  },

  methods: {
    addName() {
      this.names.push(this.newName);
      this.newName='';
    },

    toggleClass() {
      this.isLoading= true;
    },

  },

  computed: {
    reversedMessage() {
      return this.mymessage.split('').reverse().join('');
    },
    incompleteTasks(){
      return this.tasks.filter(task => ! task.completed);
    }
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

.is-loading { background : red; }
</style>
