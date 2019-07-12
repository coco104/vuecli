<template>
  <div id="app">
    <h1 class="biaoti"> todolist </h1>
    <label>添加新任务：</label>
    <input v-on:keyup.enter="addNewItem" v-model="newItem" placeholder="跑步"/>
    <button v-on:click="addNewItem">添加</button>
    <ol class="list">
      <li v-for="item in items" v-bind:class={finished:item.isFinished} v-on:click="finish(item)">
        {{item.content}}
      </li>
    </ol>
  </div>

</template>

<script>
  export default {
    name: 'HelloWorld',
    data() {
      return {
        items: [
          {
            content: '读书',
            isFinished: false
          },
          {
            content: '吃饭',
            isFinished: true
          }
        ],
        newItem: ''
      }
    },
    methods: {
      addNewItem() {    //用push将对象加进数组
        this.items.push(
          {content: this.newItem,
          isFinished: false}
        )
        this.newItem = ''  //清空
      },
      finish(item) {
        item.isFinished = !item.isFinished
      }
    }
  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .finished {
    text-decoration: line-through;
  }
  .biaoti{
    color:red;
    font-size:40px;
  }
</style>
