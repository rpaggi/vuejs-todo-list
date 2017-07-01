<template>
  <div class="list">
    <h1>{{title}}</h1>

    <input type="text" v-model="text" v-on:keyup.enter="addItem()">

    <ul>
      <li v-for="(item, index) in list" v-bind:key="index">
        {{ item.text }} <button v-on:click="delItem(index)">X</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  beforeMount () {
    this.list = [{text: 'First Item'}, {text: 'Second Item'}]
  },
  name: 'list',
  data () {
    return (
    {
      title: 'ToDo List',
      text: '',
      list: []
    }
    )
  },
  methods: {
    addItem () {
      this.list.push({text: this.text})
      this.text = ''
    },
    delItem (index) {
      this.list.splice(index, 1)
    }
  }
}
</script>
