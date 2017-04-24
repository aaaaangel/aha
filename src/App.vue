<template>
  <div id="app">
    <div id="d1"> <h1 v-text="title"></h1></div>
    <div id="d2"><input v-model="newItem" v-on:keyup.enter="addNew()"></div>
    <div id="d3"><ul>
      <li v-for="item in items" v-bind:class="{finished: item.isFinished}"
      v-on:click="toggleFinish(item)">
        {{item.label}}
      </li>
    </ul></div>
  </div>
</template>

<script>
export default {
  data: function() {
      return {
        title: 'this is a todo list',
        items: [
        ],
        newItem:'',
      }
  },
  methods: {
      toggleFinish: function(item) {
      if(!item.isFinished) {
          item.isFinished = !item.isFinished
        }
        else {
           this.items.splice(item.num,1);
        for(var i=item.num;i<this.items.length;i++)
        {
            this.items[i].num--;
        
        }}
  //item.isFinished=!item.isFinished
      },
      addNew: function () {
        this.items.push({
          label: this.newItem,
          isFinished: false,
          num: this.items.length,
    })
        this.newItem=''
      },
  }
}
</script>

<style>
  body{
    padding: 0;
    margin: 0;
  }
  
  .finished {
    text-decoration: line-through;
  }
  
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
  
  #d1{
    top: 0;
    height: 100px;
    background-color: cornsilk;
  }
  
  #d2{
  
  }
</style>
